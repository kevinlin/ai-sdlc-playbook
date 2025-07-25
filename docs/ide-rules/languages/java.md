# Java Best Practices

## IDE Configuration Headers

### For Cursor IDE

To create a new Cursor Rule:

1. Enter the name as `java`
2. Copy & paste the following header and rule content below:

```markdown
---
description: Java Best Practices
globs: **/*.java
alwaysApply: false
---
```

### For Kiro IDE

To create a new Kiro Steering Document:

1. Create a file named `java.md` in `.kiro/steering/`
2. Copy & paste the following header and rule content below:

```markdown
---
inclusion: fileMatch
fileMatchPattern: '**/*.java'
---
```

For more information about IDE rules, visit:
- [Cursor Project Rules](https://docs.cursor.com/context/rules#project-rules)
- [Kiro Steering Documents](https://github.com/kirolabs/kiro)

## Rule Content

You are an expert in Java, Spring Boot, Spring Framework, Maven, JUnit, and related Java technologies.

## Code Style and Structure
- Write clean, efficient, and well-documented Java code, providing accurate Spring Boot examples.
- Follow Spring Boot best practices and conventions in your code.
- Implement RESTful API design patterns to create web services.
- Use descriptive method and variable names following camelCase.
- Structure Spring Boot applications: controllers, services, repositories, models, configuration.

## Spring Boot Specific Requirements
- Use Spring Boot starters for quick project setup and dependency management.
- Correctly implement annotations (such as @SpringBootApplication, @RestController, @Service).
- Effectively utilize Spring Boot's auto-configuration features.
- Use @ControllerAdvice and @ExceptionHandler for proper exception handling.

## Naming Conventions
- Class names use PascalCase (e.g., UserController, OrderService).
- Method and variable names use camelCase (e.g., findUserById, isOrderValid).
- Constants use ALL_UPPER_CASE (e.g., MAX_RETRY_ATTEMPTS, DEFAULT_PAGE_SIZE).

## Java and Spring Boot Usage
- Appropriately use Java 17 or newer features (e.g., records, sealed classes, pattern matching).
- Leverage Spring Boot 3.x features and best practices.
- Use Spring Data JPA for database operations when appropriate.
- Use Bean Validation for proper validation (e.g., @Valid, custom validators).

## Configuration and Properties
- Use application.properties or application.yml for configuration.
- Use Spring configuration files for environment-specific settings.
- Use @ConfigurationProperties for type-safe configuration properties.

## Dependency Injection and IoC
- For better testability, use constructor injection instead of field injection.
- Use Spring's IoC container to manage bean lifecycles.

## Testing
- Use JUnit 5 and Spring Boot Test for unit testing.
- Use MockMvc for web layer testing.
- Use @SpringBootTest for integration testing.
- Use @DataJpaTest for repository layer testing.

## Performance and Scalability
- Use Spring Cache abstraction for caching strategies.
- Use @Async for non-blocking asynchronous operations.
- Implement proper database indexing and query optimization.

## Security
- Implement Spring Security for authentication and authorization.
- Use appropriate password encoding (e.g., BCrypt).
- Implement CORS configuration when necessary.

## Logging and Monitoring
- Use SLF4J and Logback for logging.
- Implement appropriate log levels (ERROR, WARN, INFO, DEBUG).
- Use Spring Boot Actuator for application monitoring and metrics collection.

## API Documentation
- Use Springdoc OpenAPI (formerly Swagger) for API documentation.

## Data Access and ORM
- Use Spring Data JPA for database operations.
- Implement proper entity relationships and cascading operations.
- Use tools like Flyway or Liquibase for database migrations.

## Build and Deployment
- Use Maven for dependency management and build processes.
- Implement appropriate configuration files for different environments (development, testing, production).
- Use Docker for containerization when applicable.

Follow these best practices:
- RESTful API design (proper use of HTTP methods, status codes, etc.).
- Microservices architecture (if applicable).
- Use Spring's @Async or Spring WebFlux for reactive programming and asynchronous processing.

Follow SOLID principles in Spring Boot application design to maintain high cohesion and low coupling. 