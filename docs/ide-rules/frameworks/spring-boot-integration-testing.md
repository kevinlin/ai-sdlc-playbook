# Spring Boot Integration Testing Best Practices

To create a new Cursor Rule:

1. Enter the name as `sprint-boot-integration-testing`
2. Copy & paste the file content from below

For more information, visit the [Project rules](https://docs.cursor.com/context/rules#project-rules).


```markdown
---
description: 
globs: 
alwaysApply: false
---
# Java Integration testing guidelines

These guidelines aim to ensure consistency, reliability, and maintainability of integration tests within the project.

## Implementing These Principles

These guidelines are built upon the following core principles:

- Principle 1: Test Isolation - Each integration test must be independent and not affect other tests
- Principle 2: Environment Reproducibility - Use containerized dependencies for consistent test environments  
- Principle 3: Clear Test Boundaries - Focus on integration points rather than duplicating unit test logic
- Principle 4: Performance Optimization - Balance thorough testing with execution speed
- Principle 5: Maintainable Assertions - Use specific, clear assertions that provide meaningful feedback
- Principle 6: Resource Management - Properly manage external dependencies and cleanup after tests

## Table of contents

- Rule 1: Define Clear Scope and Purpose for Integration Tests
- Rule 2: Manage Test Environment & Dependencies with Testcontainers
- Rule 3: Utilize TestRestTemplate for Robust API Testing
- Rule 4: Implement Consistent Data Management Strategies
- Rule 5: Maintain Clear Test Structure and Assertions
- Rule 6: Optimize for Performance and Ensure Proper Cleanup

## Rule 1: Define Clear Scope and Purpose for Integration Tests

Title: Clearly Define the Scope and Purpose of Each Integration Test
Description:
- Integration tests must verify the interaction between multiple components or systems (e.g., service layer with database, service-to-service communication over HTTP).
- Clearly define the boundary of each integration test. What specific interaction, contract, or flow is being tested?
- Prefer integration tests for verifying contracts between services (APIs) and interactions with external dependencies (databases, message queues, etc.).
- Avoid replicating complex business logic in integration tests if it is already thoroughly covered by unit tests. Focus on the integration points.

**Good example:**
```java
// Assume: ProductService interacts with ProductRepository (database) and NotificationService (external HTTP)

// @SpringBootTest // or similar context for the test
// @Testcontainers // if using Testcontainers
public class ProductServiceIT {
    private static final Logger log = LoggerFactory.getLogger(ProductServiceIT.class);

    // @Autowired
    // private ProductService productService;
    
    // @Autowired
    // private ProductRepository productRepository; // To verify DB state

    // Mock or use a Testcontainer for NotificationService if its actual calls are out of scope
    // @MockBean
    // private NotificationService mockNotificationService;

    // @Test
    void should_createProduct_saveToDatabase_and_sendNotification() {
        // Scope: Test the flow of creating a product, ensuring it's saved,
        // and that a notification attempt is made.

        // Given: A product DTO
        // ProductDto newProductDto = new ProductDto("Laptop X1", 1500.00);

        // When: ProductService creates the product
        // Product createdProduct = productService.createProduct(newProductDto);

        // Then: Verify interactions
        // 1. Product is saved in the database (verify via repository or direct query)
        // Optional<ProductEntity> savedEntity = productRepository.findById(createdProduct.getId());
        // assertThat(savedEntity).isPresent();
        // assertThat(savedEntity.get().getName()).isEqualTo("Laptop X1");

        // 2. Notification service was called (verify via mock or wiremock if testing HTTP contract)
        // verify(mockNotificationService).sendProductCreationNotification(any(Product.class));
        log.info("Conceptual test: Product creation flow verified.");
    }
}
```

**Bad Example:**
```java
// @SpringBootTest
public class OverlappingProductLogicIT {
    private static final Logger log = LoggerFactory.getLogger(OverlappingProductLogicIT.class);

    // @Autowired
    // private ProductService productService;

    // @Test
    void should_calculateComplexPricing_duringProductCreation() {
        // Bad: This test might be re-testing complex pricing logic
        // that should already be unit-tested in ProductService or a PricingEngine unit test.
        // The integration test should focus on whether ProductService correctly integrates
        // with the database and other services during creation, assuming pricing logic is correct.
        
        // ProductDto productWithComplexPricing = new ProductDto("ComplexItem", 10.0, List.of(new DiscountRule(...)));
        // Product createdProduct = productService.createProduct(productWithComplexPricing);
        
        // If asserts here are deeply checking specific price calculations, it's likely a unit test concern.
        // assertThat(createdProduct.getFinalPrice()).isEqualTo(9.99); // This might be too specific for an IT
        log.warn("Conceptual bad test: Replicating unit test logic for pricing.");
    }
}
```

## Rule 2: Manage Test Environment & Dependencies with Testcontainers

Title: Use Testcontainers for Reliable Management of External Dependencies
Description:
- Use Testcontainers (`org.testcontainers:testcontainers`) to manage external dependencies (databases, message brokers, caches, other services) required for the test. Avoid relying on pre-existing, shared external environments to ensure test isolation and reproducibility.
- Declare containerized dependencies using `@Testcontainers` and `@Container` annotations for JUnit 5 integration (`org.testcontainers:junit-jupiter`). Manage container lifecycles appropriately (per test suite using `static @Container` or per test method, favoring suite-level for performance).
- Use official or well-maintained Docker images for dependencies. Pin image versions (e.g., `"postgres:15-alpine"`) to ensure reproducible builds.
- Configure containers programmatically (ports, environment variables, wait strategies) within the test setup. Use `Wait.for...` strategies (e.g., `Wait.forHttp("/health")`, `Wait.forLogMessage(...)`) to ensure containers are ready before tests run.
- Inject dynamic container properties (like mapped ports or JDBC URLs) into the application context or test configuration. For Spring Boot, use `@DynamicPropertySource` with a static method. For others, manually retrieve properties in setup methods.

**Good example:**
```java
import org.junit.jupiter.api.Test;
import org.slf4j.Logger;
import org.slf4j.LoggerFactory;
import org.springframework.boot.test.context.SpringBootTest;
import org.springframework.test.context.DynamicPropertyRegistry;
import org.springframework.test.context.DynamicPropertySource;
import org.testcontainers.containers.PostgreSQLContainer;
import org.testcontainers.junit.jupiter.Container;
import org.testcontainers.junit.jupiter.Testcontainers;
import static org.assertj.core.api.Assertions.assertThat; // For assertion

@Testcontainers
@SpringBootTest // Or relevant test context setup
class MyRepositoryIT {
    private static final Logger log = LoggerFactory.getLogger(MyRepositoryIT.class);

    @Container // Static -> shared container for all tests in this class
    static PostgreSQLContainer<?> postgres = new PostgreSQLContainer<>("postgres:15-alpine")
            .withDatabaseName("testdb")
            .withUsername("testuser")
            .withPassword("testpass");
            // .waitingFor(Wait.forListeningPort()); // Default wait strategy is often sufficient for DBs

    // Dynamically set properties based on container info
    @DynamicPropertySource
    static void configureProperties(DynamicPropertyRegistry registry) {
        registry.add("spring.datasource.url", postgres::getJdbcUrl);
        registry.add("spring.datasource.username", postgres::getUsername);
        registry.add("spring.datasource.password", postgres::getPassword);
        registry.add("spring.jpa.hibernate.ddl-auto", () -> "create-drop");
    }

    // Inject your repository/service here
    // @Autowired
    // private MyRepository repository;

    @Test
    void should_connectAndInteractWithDatabase() {
        // Test logic interacting with the repository,
        // which uses the Testcontainer database
        assertThat(postgres.isRunning()).isTrue();
        log.info("PostgreSQL container is running on JDBC URL: {}", postgres.getJdbcUrl());
        // ... perform repository operations and assertions ...
        // Example: MyEntity entity = new MyEntity("testData");
        // repository.save(entity);
        // Optional<MyEntity> found = repository.findById(entity.getId());
        // assertThat(found).isPresent();
    }
}
```

**Bad Example:**
```java
// @SpringBootTest
public class MyServiceReliesOnExternalDbIT {
    private static final Logger log = LoggerFactory.getLogger(MyServiceReliesOnExternalDbIT.class);

    // @Autowired
    // private MyDataService dataService;

    // No Testcontainers. This test assumes an external PostgreSQL server
    // is running on localhost:5432 with specific credentials and schema.
    // spring.datasource.url=jdbc:postgresql://localhost:5432/mydb_dev
    // spring.datasource.username=dev_user
    // spring.datasource.password=dev_secret

    // @Test
    void should_fetchDataFromPreConfiguredExternalDatabase() {
        // Bad: Test depends on an external, manually configured database.
        // - Not isolated: Other tests or developers might change the DB state.
        // - Not reproducible: Fails if DB is down, schema changes, or on CI without the DB.
        // - Hard to manage data state between tests.
        // List<Data> data = dataService.findAll();
        // assertThat(data).isNotEmpty(); // This might pass or fail based on external DB state.
        log.warn("Conceptual bad test: Relies on external, shared database.");
    }
}
```

## Rule 3: Utilize TestRestTemplate for Robust API Testing

Title: Employ TestRestTemplate for Testing RESTful APIs Following Arrange/Act/Assert
Description:
- Use Spring Boot's `TestRestTemplate` (provided by `spring-boot-starter-test`) for testing RESTful APIs in integration tests.
- Structure tests using the Arrange/Act/Assert pattern:
    - **Arrange**: Set up request data, headers, authentication, and test prerequisites.
    - **Act**: Perform the HTTP request using TestRestTemplate methods (`getForEntity()`, `postForEntity()`, `exchange()`, etc.).
    - **Assert**: Validate the response (status code, headers, response body) using AssertJ or JUnit assertions.
- Always validate the HTTP status code first using `ResponseEntity.getStatusCode()`.
- Use AssertJ assertions for clear and fluent validation of response content. Be specific but avoid overly brittle assertions (e.g., don't assert entire large JSON bodies if only a few fields matter).
- Configure TestRestTemplate in a `@BeforeEach` method or inject it via `@Autowired`. For custom configurations (authentication, headers), use `TestRestTemplate.withBasicAuth()` or create `HttpEntity` with custom headers.
- Handle authentication consistently using TestRestTemplate's built-in methods or by setting appropriate headers in `HttpEntity`.
- For complex request/response bodies, use POJOs that will be automatically serialized/deserialized by Spring's message converters (Jackson by default).

**Good example:**
```java
import org.junit.jupiter.api.Test;
import org.slf4j.Logger;
import org.slf4j.LoggerFactory;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.boot.test.context.SpringBootTest;
import org.springframework.boot.test.web.client.TestRestTemplate;
import org.springframework.boot.test.web.server.LocalServerPort;
import org.springframework.http.HttpEntity;
import org.springframework.http.HttpHeaders;
import org.springframework.http.HttpStatus;
import org.springframework.http.MediaType;
import org.springframework.http.ResponseEntity;

import static org.assertj.core.api.Assertions.assertThat;

// Assuming a simple DTO for request/response
class ResourceDto {
    public int id;
    public String name;
    public String data;
    public ResourceDto() {}
    public ResourceDto(int id, String name, String data) { this.id = id; this.name = name; this.data = data;}
}

@SpringBootTest(webEnvironment = SpringBootTest.WebEnvironment.RANDOM_PORT)
// Assume a controller exists at /resources that uses ResourceDto
// and has GET /resources/{id}, POST /resources
class MyApiControllerIT {

    @LocalServerPort
    private int port;

    @Autowired
    private TestRestTemplate restTemplate;

    @Test
    void getResourceById_shouldReturnOkAndResource() {
        // Arrange: Set up the expected resource ID
        int resourceId = 123;

        // Act: Perform GET request
        ResponseEntity<ResourceDto> response = restTemplate.getForEntity(
            "/resources/{id}", 
            ResourceDto.class, 
            resourceId
        );

        // Assert: Validate response
        assertThat(response.getStatusCode()).isEqualTo(HttpStatus.OK);
        assertThat(response.getBody()).isNotNull();
        assertThat(response.getBody().id).isEqualTo(123);
        assertThat(response.getBody().name).contains("ResourceName"); // Flexible assertion
        assertThat(response.getHeaders().getContentType()).isEqualTo(MediaType.APPLICATION_JSON);
    }

    @Test
    void createResource_shouldReturnCreatedAndResourceLocation() {
        // Arrange: Set up request data and headers
        ResourceDto newResource = new ResourceDto(0, "New Item", "Some data");
        HttpHeaders headers = new HttpHeaders();
        headers.setContentType(MediaType.APPLICATION_JSON);
        HttpEntity<ResourceDto> request = new HttpEntity<>(newResource, headers);

        // Act: Perform POST request
        ResponseEntity<ResourceDto> response = restTemplate.postForEntity(
            "/resources", 
            request, 
            ResourceDto.class
        );

        // Assert: Validate response
        assertThat(response.getStatusCode()).isEqualTo(HttpStatus.CREATED);
        assertThat(response.getBody()).isNotNull();
        assertThat(response.getBody().id).isNotNull(); // Assert that an ID was generated
        assertThat(response.getBody().name).isEqualTo("New Item");
        assertThat(response.getHeaders().getLocation()).isNotNull();
        assertThat(response.getHeaders().getLocation().toString()).contains("/resources/");
    }
}
```

**Bad Example:**
```java
import org.junit.jupiter.api.Test;
import org.slf4j.Logger;
import org.slf4j.LoggerFactory;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.boot.test.web.client.TestRestTemplate;
import org.springframework.http.ResponseEntity;
import static org.assertj.core.api.Assertions.assertThat;

// @SpringBootTest(webEnvironment = SpringBootTest.WebEnvironment.RANDOM_PORT)
public class ApiTestAntiPatternsIT {
    private static final Logger log = LoggerFactory.getLogger(ApiTestAntiPatternsIT.class);

    // @Autowired private TestRestTemplate restTemplate;

    @Test
    void getResource_badAssertions() {
        // Bad: Not checking status code first or at all.
        // Bad: Extracting entire response as string and doing string manipulations.
        // ResponseEntity<String> response = restTemplate.getForEntity("/resources/1", String.class);
        // String responseBody = response.getBody();
        // assertThat(responseBody).contains("\"id\":1"); // Brittle, hard to read, no status check
        
        // Bad: Overly specific assertions on large JSON strings.
        // assertThat(responseBody).isEqualTo("{very long and complex json string...}"); // Brittle
        log.warn("Conceptual bad API test: Poor assertions, missing status code check.");
    }

    @Test
    void createResource_noBodyValidation() {
        // Bad: Not validating the structure or content of the response body upon creation.
        // ResourceDto newResource = new ResourceDto(0, "Test", "data");
        // ResponseEntity<Void> response = restTemplate.postForEntity("/resources", newResource, Void.class);
        // assertThat(response.getStatusCode().value()).isEqualTo(201); // Only checks status code, ignores response body
        log.warn("Conceptual bad API test: Missing response body validation.");
    }
}
```

## Rule 4: Implement Consistent Data Management Strategies

Title: Ensure Controlled and Isolated Data States for Each Test
Description:
- Each integration test must run with a known, controlled data state to ensure reliability and prevent interference between tests. Tests must be independent.
- Seed necessary test data before each test (`@BeforeEach`) or test suite (`@BeforeAll`). Options include:
    - **Application Services:** Call repository or service methods to set up required entities.
    - **Object Mothers / Test Data Builders:** Use patterns to create complex test data objects easily and consistently.
    - **SQL Scripts:** Use `@Sql` (Spring) or execute scripts via JDBC/Testcontainers `execInContainer()` for setup.
- Clean up persistent data created during a test run to ensure test isolation. Choose one primary strategy:
    - **Transaction Rollback:** (Preferred for simplicity if applicable, e.g., Spring Test with `@Transactional`) Annotate test methods or the class. Spring Test will automatically roll back the transaction after each test for database operations within that transaction.
    - **Truncate/Delete Tables:** Execute `TRUNCATE TABLE ...` or `DELETE FROM ...` statements in `@AfterEach` or via Testcontainers. Fastest for complex state reset if transactions are not manageable across all interactions.
    - **Delete Specific Data:** Use repository/service methods in `@AfterEach` to delete only the data created by the test (can be complex to track and error-prone).
    - **Container Recreation:** Recreate the database container per test or class (very slow, generally avoided unless absolutely necessary for complete isolation between test classes).

**Good example:**
(Using Spring Test `@Transactional` for rollback)
```java
import org.junit.jupiter.api.Test;
import org.slf4j.Logger;
import org.slf4j.LoggerFactory;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.boot.test.context.SpringBootTest;
import org.springframework.transaction.annotation.Transactional;
// Assume Entity: Item with id, name
// Assume Repository: ItemRepository extends JpaRepository<Item, Long>

// @Testcontainers // If DB is managed by Testcontainers
// @SpringBootTest
// @Transactional // This will roll back transactions after each test method
public class ItemRepositoryTransactionalIT {
    private static final Logger log = LoggerFactory.getLogger(ItemRepositoryTransactionalIT.class);

    // @Autowired
    // private ItemRepository itemRepository;

    // @Test
    void should_saveAndRetrieveItem() {
        // Item newItem = new Item("Test Item");
        // Item savedItem = itemRepository.save(newItem);
        // assertThat(savedItem.getId()).isNotNull();
        
        // Optional<Item> foundItem = itemRepository.findById(savedItem.getId());
        // assertThat(foundItem).isPresent();
        // assertThat(foundItem.get().getName()).isEqualTo("Test Item");
        log.info("Conceptual test: Save and retrieve with @Transactional rollback.");
        // Data inserted here will be rolled back automatically after this test method.
    }

    // @Test
    void should_findNoItems_ifNoneSavedInThisTest() {
        // List<Item> items = itemRepository.findAll();
        // assertThat(items).isEmpty();
        log.info("Conceptual test: Ensuring test isolation via @Transactional.");
        // Due to rollback from other tests, this test starts with a clean state (within its transaction).
    }
}
```

**Bad Example:**
```java
// @SpringBootTest
// @Testcontainers
public class ItemRepositoryNoCleanupIT {
    private static final Logger log = LoggerFactory.getLogger(ItemRepositoryNoCleanupIT.class);
    
    // @Autowired 
    // private ItemRepository itemRepository;
    private static Long sharedItemId; // Bad: Sharing state between tests via static field

    // @Test // Assume tests run in unpredictable order
    void testA_createItem() {
        // Item item = new Item("Shared Item");
        // item = itemRepository.save(item);
        // sharedItemId = item.getId();
        // assertThat(itemRepository.count()).isGreaterThan(0);
        log.warn("Conceptual bad test A: Creates data that might affect other tests.");
    }

    // @Test
    void testB_checkIfItemExists() {
        // Bad: This test's success depends on testA_createItem() having run first
        // and no cleanup being performed. This leads to flaky and order-dependent tests.
        // if (sharedItemId != null) {
        //    Optional<Item> item = itemRepository.findById(sharedItemId);
        //    assertThat(item).isPresent(); 
        // } else {
        //    List<Item> items = itemRepository.findAll();
        //    assertThat(items.stream().anyMatch(i -> i.getName().equals("Shared Item"))).isTrue(); // Brittle check
        // }
        log.warn("Conceptual bad test B: Depends on data from another test due to no cleanup.");
    }
}
```

## Rule 5: Maintain Clear Test Structure and Assertions

Title: Structure Integration Tests Clearly and Use Specific Assertions
Description:
- Keep integration tests focused on a single user story, API endpoint interaction, or component integration scenario.
- Use descriptive test method names (e.g., `should_ExpectedBehavior_when_StateUnderTest`) or JUnit 5's `@DisplayName` annotation to clearly explain the scenario being tested.
- Assertions should be specific and provide clear failure messages.
    - **TestRestTemplate:** Use AssertJ assertions for clear validation of response status, headers, and body content (e.g., `assertThat(response.getBody().fieldName).isEqualTo(expectedValue)`).
    - **Database State:** Use repositories or JDBC to fetch data after the action and assert its state using libraries like AssertJ for fluent and readable assertions.
- For debugging, consider logging response details in test methods during development, but remove verbose logging in committed code to keep test output clean and focus on assertion failures.

**Good example:**
```java
import org.junit.jupiter.api.DisplayName;
import org.junit.jupiter.api.Test;
import org.slf4j.Logger;
import org.slf4j.LoggerFactory;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.boot.test.context.SpringBootTest;
import org.springframework.boot.test.web.client.TestRestTemplate;
import org.springframework.http.HttpEntity;
import org.springframework.http.HttpHeaders;
import org.springframework.http.HttpStatus;
import org.springframework.http.MediaType;
import org.springframework.http.ResponseEntity;
import static org.assertj.core.api.Assertions.assertThat;

class UserDto {
    public Long id;
    public String username;
    public String email;
    public UserDto() {}
    public UserDto(String username, String email) { this.username = username; this.email = email; }
}

@SpringBootTest(webEnvironment = SpringBootTest.WebEnvironment.RANDOM_PORT)
public class UserRegistrationIT {
    private static final Logger log = LoggerFactory.getLogger(UserRegistrationIT.class);
    
    // @Autowired private UserRepository userRepository;
    // @Autowired private TestRestTemplate restTemplate;

    @Test
    @DisplayName("POST /users with valid data should create user, return 201, and user details")
    void postUsers_withValidData_shouldCreateUserAndReturn201() {
        // Arrange: Prepare request data
        // UserDto newUser = new UserDto("testuser", "test@example.com");
        // HttpHeaders headers = new HttpHeaders();
        // headers.setContentType(MediaType.APPLICATION_JSON);
        // HttpEntity<UserDto> request = new HttpEntity<>(newUser, headers);
        
        // Act: Send POST request
        // ResponseEntity<UserDto> response = restTemplate.postForEntity("/users", request, UserDto.class);
        
        // Assert: Validate API response
        // assertThat(response.getStatusCode()).isEqualTo(HttpStatus.CREATED);
        // assertThat(response.getBody()).isNotNull();
        // assertThat(response.getBody().username).isEqualTo("testuser");
        // assertThat(response.getBody().email).isEqualTo("test@example.com");
        // assertThat(response.getBody().id).isNotNull();

        // Verify database state (using AssertJ for fluent assertions)
        // Long newUserId = response.getBody().id;
        // Optional<UserEntity> createdUser = userRepository.findById(newUserId);
        // assertThat(createdUser).isPresent();
        // assertThat(createdUser.get().getEmail()).isEqualTo("test@example.com");
        log.info("Conceptual good test: Clear name, focused scope, specific assertions.");
    }
}
```

**Bad Example:**
```java
// @SpringBootTest(webEnvironment = SpringBootTest.WebEnvironment.RANDOM_PORT)
public class VagueUserActionsIT {
    private static final Logger log = LoggerFactory.getLogger(VagueUserActionsIT.class);
    
    // @Autowired private TestRestTemplate restTemplate;
    
    // @Test
    void testUserActions() { // Bad: Vague test name, unclear scope
        // This test might try to do too many things:
        // 1. Create a user
        // restTemplate.postForEntity("/users", userDto, UserDto.class); // No assertions
        
        // 2. Update the user
        // restTemplate.put("/users/1", updatedUserDto); // No return value validation
        
        // 3. Fetch the user and verify all fields
        // ResponseEntity<String> response = restTemplate.getForEntity("/users/1", String.class);
        // String responseBody = response.getBody();
        // Bad: Asserting a large string is brittle.
        // assertThat(responseBody).isEqualTo("{ \"id\":1, \"name\":\"updated\", ... very_long_json ... }"); // Should use specific field assertions instead
        
        // 4. Delete the user
        // restTemplate.delete("/users/1"); // No status code validation
        log.warn("Conceptual bad test: Vague name, too broad, brittle assertions.");
        // Problem: If one part fails, it's hard to know which interaction broke.
        // Assertions are not specific enough or are too brittle.
    }
}
```

## Rule 6: Optimize for Performance and Ensure Proper Cleanup

Title: Be Mindful of Integration Test Performance and Resource Cleanup
Description:
- Be mindful of integration test execution time. Container startup is often the main overhead.
    - **Prefer static `@Container` fields:** This reuses the same container for all tests within a class, significantly speeding up test suites.
    - **Consider Singleton Container Pattern:** For sharing a container across multiple test classes (more advanced setup, use with caution to maintain isolation if state leaks).
- Ensure Testcontainers resources are stopped and removed after the test suite finishes. The `testcontainers-junit-jupiter` extension handles this automatically for containers managed via `@Container`. If managing containers manually, ensure `stop()` is called in a suitable cleanup hook (e.g., `@AfterAll` or a JVM shutdown hook for true singletons).
- Separate integration tests (e.g., `*IT.java` or `*IntegrationTest.java`) from unit tests (`*Test.java`) using naming conventions. Configure build tools (Maven Surefire/Failsafe, Gradle) to run them in different phases or tasks if needed (integration tests often run after the application is packaged).

**Good example:**
(Using static @Container for performance and automatic cleanup by junit-jupiter extension)
```java
import org.junit.jupiter.api.AfterAll;
import org.junit.jupiter.api.BeforeAll;
import org.junit.jupiter.api.Test;
import org.slf4j.Logger;
import org.slf4j.LoggerFactory;
import org.testcontainers.containers.GenericContainer;
import org.testcontainers.junit.jupiter.Container;
import org.testcontainers.junit.jupiter.Testcontainers;
import org.testcontainers.utility.DockerImageName;
import static org.assertj.core.api.Assertions.assertThat; // For assertion

@Testcontainers
public class MyServiceWithSharedContainerIT {
    private static final Logger log = LoggerFactory.getLogger(MyServiceWithSharedContainerIT.class);

    // Good: Static container is started once for all tests in this class
    @Container
    static GenericContainer<?> redis = new GenericContainer<>(DockerImageName.parse("redis:6-alpine"))
            .withExposedPorts(6379);

    @BeforeAll
    static void beforeAll() {
        log.info("Redis container started for suite: {}:{}", redis.getContainerIpAddress(), redis.getMappedPort(6379));
        // Setup SUT to use redis.getMappedPort(6379) etc.
    }

    @Test
    void testOperationOne_usesRedis() {
        assertThat(redis.isRunning()).isTrue();
        // ... test logic interacting with service that uses Redis ...
        log.info("Test one with shared Redis.");
    }

    @Test
    void testOperationTwo_usesRedis() {
        assertThat(redis.isRunning()).isTrue();
        // ... another test logic ...
        log.info("Test two with shared Redis.");
    }

    // @AfterAll // Not strictly needed for @Container, as Testcontainers extension handles stop()
    // static void afterAll() {
    //    log.info("Suite finished, Testcontainers will stop the Redis container.");
    // }
}
```

**Bad Example:**
```java
import org.junit.jupiter.api.AfterEach;
import org.junit.jupiter.api.BeforeEach;
import org.junit.jupiter.api.Test;
import org.slf4j.Logger;
import org.slf4j.LoggerFactory;
import org.testcontainers.containers.GenericContainer;
import org.testcontainers.utility.DockerImageName;

// @Testcontainers // Annotation might be missing or misused
public class MyServiceWithPerMethodContainerIT {
    private static final Logger log = LoggerFactory.getLogger(MyServiceWithPerMethodContainerIT.class);

    // Bad: Non-static @Container (or manual management per method) starts a new container for EACH test method.
    // This is very slow for multiple tests.
    // @Container // If this were not static, it would be per-method if @Testcontainers is on class
    private GenericContainer<?> redisPerMethod; 

    // @BeforeEach // Manual start/stop per method is slow and error-prone
    void setUpPerMethod() {
        redisPerMethod = new GenericContainer<>(DockerImageName.parse("redis:5-alpine"))
                            .withExposedPorts(6379);
        redisPerMethod.start(); // Manual start
        log.info("Redis started for method at port: {}", redisPerMethod.getMappedPort(6379));
    }

    // @Test
    void testA() {
        // assertThat(redisPerMethod.isRunning()).isTrue();
        log.info("Test A using its own Redis instance.");
    }

    // @Test
    void testB() {
        // assertThat(redisPerMethod.isRunning()).isTrue();
        log.warn("Test B using its own Redis instance (slow!).");
    }

    // @AfterEach
    void tearDownPerMethod() {
        if (redisPerMethod != null) {
            redisPerMethod.stop(); // Manual stop needed
            log.info("Redis stopped for method.");
        }
    }
    // Problem: Significant performance degradation due to container restart for every test.
    // Also, higher risk of resource leaks if stop() is missed or fails.
}
```

---
This rule serves as a starting point. Refer to authoritative resources on Java Integration Testing, Testcontainers, and Spring Boot's TestRestTemplate for more in-depth understanding and application.
```