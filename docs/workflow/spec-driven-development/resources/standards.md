# Standards and Methodology References

<!-- Navigation Metadata -->
<!-- Resource: Standards | Level: Reference | Prerequisites: None -->
<!-- Related: process/requirements-phase.md, templates/requirements-template.md, examples/simple-feature-spec.md -->

**📍 You are here:** [Main Guide](../../README.md) → [Resources](README.md) → **Standards**

## Quick Navigation
- **📋 Apply EARS:** [Requirements Phase](../process/requirements-phase.md) - Use EARS format in practice
- **📝 Use Template:** [Requirements Template](../templates/requirements-template.md) - EARS-formatted template
- **📖 See Examples:** [Simple Feature Specs](../examples/simple-feature-spec.md) - EARS in action
- **🔧 More Tools:** [Tools & Resources](tools.md) - Additional helpful resources

---

This section provides detailed information about industry standards, methodologies, and best practices that inform the spec-driven development approach.

## EARS (Easy Approach to Requirements Syntax)

EARS is a structured approach to writing requirements that makes them clear, testable, and unambiguous. It uses specific keywords to define different types of requirements.

### EARS Keywords and Structure

#### WHEN (Event-driven requirements)
Used for requirements triggered by specific events or conditions.

**Format:** `WHEN [event/trigger] THEN [system] SHALL [response]`

**Examples:**
- WHEN a user clicks the "Save" button THEN the system SHALL validate all form fields
- WHEN a file upload exceeds 10MB THEN the system SHALL display an error message
- WHEN a user session expires THEN the system SHALL redirect to the login page

#### IF (State-driven requirements)
Used for requirements that depend on specific system states or conditions.

**Format:** `IF [condition] THEN [system] SHALL [response]`

**Examples:**
- IF a user is not authenticated THEN the system SHALL deny access to protected resources
- IF the database connection fails THEN the system SHALL display a maintenance message
- IF a user has admin privileges THEN the system SHALL show the admin panel

#### WHILE (Continuous requirements)
Used for requirements that must be maintained during ongoing operations.

**Format:** `WHILE [condition] [system] SHALL [continuous behavior]`

**Examples:**
- WHILE a file is uploading the system SHALL display a progress indicator
- WHILE a user is typing the system SHALL provide real-time validation feedback
- WHILE the system is processing a request the system SHALL prevent duplicate submissions

#### WHERE (Optional requirements)
Used for requirements that apply only in specific contexts or locations.

**Format:** `WHERE [location/context] [system] SHALL [behavior]`

**Examples:**
- WHERE the user is on a mobile device the system SHALL use responsive layout
- WHERE the application runs in production mode the system SHALL log errors to external service
- WHERE multiple users edit simultaneously the system SHALL handle conflicts gracefully

### EARS Best Practices

1. **Use Active Voice**: Write requirements using active voice for clarity
2. **Be Specific**: Avoid vague terms like "user-friendly" or "fast"
3. **One Requirement Per Statement**: Each EARS statement should contain exactly one requirement
4. **Testable Outcomes**: Every requirement should be verifiable through testing
5. **Consistent Terminology**: Use the same terms throughout all requirements

### EARS Anti-Patterns to Avoid

- **Compound Requirements**: Avoid multiple SHALL statements in one requirement
- **Vague Conditions**: Don't use unclear triggers like "when appropriate"
- **Implementation Details**: Focus on what, not how
- **Untestable Requirements**: Avoid subjective terms that can't be measured

## System Design and Architecture Best Practices

### Architectural Principles

#### SOLID Principles
- **Single Responsibility**: Each module has one reason to change
- **Open/Closed**: Open for extension, closed for modification
- **Liskov Substitution**: Subtypes must be substitutable for base types
- **Interface Segregation**: Clients shouldn't depend on unused interfaces
- **Dependency Inversion**: Depend on abstractions, not concretions

#### Design Patterns
- **Creational**: Factory, Builder, Singleton
- **Structural**: Adapter, Decorator, Facade
- **Behavioral**: Observer, Strategy, Command

#### Architectural Styles
- **Layered Architecture**: Separation of concerns through layers
- **Microservices**: Distributed system of small, independent services
- **Event-Driven**: Components communicate through events
- **Hexagonal**: Isolates core logic from external concerns

### System Design Methodologies

#### Domain-Driven Design (DDD)
- **Ubiquitous Language**: Shared vocabulary between technical and domain experts
- **Bounded Contexts**: Clear boundaries around domain models
- **Aggregates**: Consistency boundaries for business rules
- **Domain Events**: Capture important business occurrences

#### Clean Architecture
- **Independence**: Framework, database, and UI independent
- **Testability**: Business rules can be tested without external elements
- **UI Independence**: UI can change without changing business rules
- **Database Independence**: Business rules not bound to database

#### Twelve-Factor App
1. **Codebase**: One codebase tracked in revision control
2. **Dependencies**: Explicitly declare and isolate dependencies
3. **Config**: Store config in the environment
4. **Backing Services**: Treat backing services as attached resources
5. **Build, Release, Run**: Strictly separate build and run stages
6. **Processes**: Execute as one or more stateless processes
7. **Port Binding**: Export services via port binding
8. **Concurrency**: Scale out via the process model
9. **Disposability**: Maximize robustness with fast startup and graceful shutdown
10. **Dev/Prod Parity**: Keep development, staging, and production as similar as possible
11. **Logs**: Treat logs as event streams
12. **Admin Processes**: Run admin/management tasks as one-off processes

## Requirements Engineering Methodologies

### Agile Requirements Engineering

#### User Stories
**Format:** `As a [role], I want [feature], so that [benefit]`

**Characteristics:**
- **Independent**: Can be developed separately
- **Negotiable**: Details can be discussed and refined
- **Valuable**: Provides value to users or business
- **Estimable**: Can be sized for planning
- **Small**: Can be completed in one iteration
- **Testable**: Has clear acceptance criteria

#### Acceptance Criteria
- Define when a user story is complete
- Written in Given-When-Then format or EARS format
- Should be testable and specific
- Agreed upon by team and stakeholders

### Behavior-Driven Development (BDD)

#### Gherkin Syntax
```gherkin
Feature: User Authentication
  As a user
  I want to log into the system
  So that I can access my personal data

  Scenario: Successful login
    Given I am on the login page
    When I enter valid credentials
    Then I should be redirected to the dashboard
```

#### BDD Process
1. **Discovery**: Explore and understand requirements
2. **Formulation**: Document examples and scenarios
3. **Automation**: Create executable specifications

### Model-Based Requirements Engineering

#### Use Case Modeling
- **Actors**: External entities that interact with the system
- **Use Cases**: Specific interactions or functions
- **Relationships**: Include, extend, and generalization

#### Requirements Modeling Techniques
- **Entity-Relationship Diagrams**: Data relationships
- **State Diagrams**: System behavior over time
- **Sequence Diagrams**: Interaction between components
- **Activity Diagrams**: Workflow and process flow

---

[← Back to Resources](README.md) | [Tools and Templates →](../templates/README.md)