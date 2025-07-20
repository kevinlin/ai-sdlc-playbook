# 1.2 Technical Specification

This section provides a structured approach to creating detailed technical specifications for an AI-powered development workflow. Technical specifications define how the system will be implemented, focusing on data models, API endpoints, backend architecture, and technical implementation details.

The technical specification should be created after the [Functional Requirements](01-functional-requirement.md) have been defined and approved, as it translates the functional needs into technical implementation details.

## 1. Define the Data Model

Once you have detailed functional requirements, use an LLM to create a detailed data model. If the data model is not correct and does not follow the logic of your business requirements at this early stage, then it's unlikely the end result of the development process will function as expected. A data model also gives the LLMs guidance later in the process on how to structure code and models to conform to the data being stored, processed and retrieved.

Use the following prompt to define the data model, use an advanced reasoning model, such as a 'thinking' model for all heavy analysis technical work:

```
I'd like to create a data model based on the following functional requirements and technical needs.

ANALYSIS PHASE:

Read, analyze and understand the following functional requirements:

[PASTE THE FUNCTIONAL REQUIREMENTS HERE]

Ask any follow up questions that will clear up any ambiguities if needed.

IMPLEMENTATION PHASE:

Think about the above requirements and work out a simplified data model suitable for use with [MongoDB/PostgreSQL/your chosen database]. Also produce a Mermaid diagram so it is understandable in a relational format. Feel free to change labels or column names to be more clear if needed if they are more logical. The data model should be in a single, downloadable file using markdown formatting.

Consider the following technical aspects:
- Data relationships and foreign keys
- Indexing requirements for performance
- Data validation rules
- Scalability considerations
- Data migration and versioning
- Security and privacy requirements

VERIFICATION AND COMPLETION PHASE:

- Make sure the final model covers all the functional requirements
- Ensure the model is optimized for the expected query patterns
- Highlight any areas where you have made assumptions
- Include recommendations for database configuration
```

Once it produces a data model, review the data model thoroughly with your team to ensure it covers the overall intent and any edge cases are picked up. Again, if the data model is wrong, then your app will be wrong.

## 2. Backend Architecture and Technical Requirements

Define the backend architecture and technical requirements that will support your functional requirements:

### 2.1. Backend System Requirements

- Outline the backend changes necessary to support the features, including:
    - Details of new or modified APIs/endpoints.
    - Data processing and business logic requirements.
    - Security considerations, such as authentication and authorisation.
    - Performance and scalability requirements.
    - Integration patterns with external systems.

### 2.2. Data Processing and Business Logic

- Define the core business logic and data processing requirements:
    - Data validation and transformation rules.
    - Business rule implementations.
    - Workflow and state management.
    - Event handling and notifications.
    - Background job processing requirements.

### 2.3. Security and Compliance

- Specify security requirements including:
    - Authentication and authorization mechanisms.
    - Data encryption requirements (at rest and in transit).
    - API security patterns.
    - Audit logging requirements.
    - Compliance considerations (GDPR, accessibility, etc.).

### 2.4. Performance and Scalability

- Define performance requirements:
    - Expected load and concurrent user capacity.
    - Response time requirements.
    - Database performance optimization.
    - Caching strategies.
    - Monitoring and alerting requirements.

## 3. API Endpoints Requirements

If using an API for your backend, generate API endpoint requirements based on your refined data model:

Run the following prompt, use an advanced reasoning model:

```
Given the attached data model and functional requirements, please create detailed requirements for API endpoints that follow RESTful conventions. Please also include examples of the request/response objects for each endpoint.

FUNCTIONAL REQUIREMENT:
[PASTE FUNCTIONAL REQUIREMENT HERE]

DATA MODEL:
[PASTE DATA MODEL HERE]

Please create API specifications that include:

EXAMPLE FORMAT:
## API Endpoints

All endpoints follow RESTful conventions. Below is a complete list of endpoints with detailed specifications.

### [Resource Name] Endpoints

#### **Endpoint:** `/api/v1/[resource-plural]`
- **POST request:**  
  Creates a new [resource] object with all the fields passed in the body; returns the newly created object from the database.
  - Request body example: [JSON example]
  - Response example: [JSON example]
  - Status codes: 201 (Created), 400 (Bad Request), 401 (Unauthorized)
  
- **GET request:**  
  Returns a list of all [resource] objects stored in the database.
  - Query parameters: pagination, filtering, sorting options
  - Response example: [JSON example with pagination]
  - Status codes: 200 (OK), 401 (Unauthorized)

#### **Endpoint:** `/api/v1/[resource-plural]/{id}`
- **GET request:**  
  Returns the [resource] object for the given id.
  - Response example: [JSON example]
  - Status codes: 200 (OK), 404 (Not Found), 401 (Unauthorized)
  
- **PUT request:**  
  Updates the [resource] object for the given id with the fields provided in the request body; returns the updated object.
  - Request body example: [JSON example]
  - Response example: [JSON example]
  - Status codes: 200 (OK), 404 (Not Found), 400 (Bad Request)
  
- **DELETE request:**  
  Deletes the [resource] object for the given id and returns a success message.
  - Response example: [JSON example]
  - Status codes: 200 (OK), 404 (Not Found), 401 (Unauthorized)

For each endpoint, also specify:
- Authentication requirements
- Rate limiting considerations
- Validation rules
- Error response formats
- Any special business logic or constraints

DATA MODEL:
[PASTE DATA MODEL HERE]
```

Review the API endpoints with the team. Refine and re-prompt if required. Save the API endpoint requirements for later reference.

## 4. Technical Architecture Design

Define the overall technical architecture that will support your system:

### 4.1. System Architecture

Use the following prompt to create a comprehensive technical architecture:

```
Based on the following functional requirements, data model, and API specifications, create a detailed technical architecture document:

FUNCTIONAL REQUIREMENT:
[PASTE FUNCTIONAL REQUIREMENT HERE]

DATA MODEL:
[PASTE DATA MODEL HERE]

API ENDPOINTS:
[PASTE API ENDPOINTS HERE]

Please create a technical architecture that includes:

# System Architecture Overview
- High-level system components and their interactions
- Technology stack recommendations
- Deployment architecture (development, staging, production)
- Infrastructure requirements

# Application Architecture
- Backend service architecture (microservices vs monolith)
- Database architecture and data flow
- API gateway and service mesh considerations
- Authentication and authorization architecture

# Integration Architecture
- External system integrations
- Message queuing and event-driven patterns
- File storage and content delivery
- Monitoring and logging architecture

# Security Architecture
- Security layers and controls
- Data protection mechanisms
- API security patterns
- Compliance and audit requirements

# Performance and Scalability
- Caching strategies
- Database optimization
- Load balancing and auto-scaling
- Performance monitoring

Please include Mermaid diagrams where appropriate to illustrate the architecture.
```

### 4.2. Technology Stack Selection

Document the recommended technology stack including:
- Programming languages and frameworks
- Database technologies
- Infrastructure and deployment tools
- Monitoring and logging solutions
- Development and testing tools

## 5. Implementation Guidelines

Create detailed implementation guidelines for developers:

### 5.1. Development Standards

- Coding standards and conventions
- Code review requirements
- Testing strategies (unit, integration, end-to-end)
- Documentation requirements
- Version control and branching strategies

### 5.2. Database Implementation

- Database schema creation scripts
- Migration strategies
- Indexing and optimization guidelines
- Backup and recovery procedures
- Data seeding and test data management

### 5.3. API Implementation

- API versioning strategy
- Error handling patterns
- Logging and monitoring requirements
- Rate limiting implementation
- API documentation standards

## 6. Deep Technical Analysis

Using your technical specifications, conduct a deep analysis to evaluate the technical approach. Run the following prompt for meta analysis, use an advanced reasoning model:

```
Do some meta analysis to analyze the following technical specifications, focusing on technical feasibility, scalability, maintainability, and implementation complexity.

ANALYSIS PHASE:

Read, analyze and understand the following technical specifications:

DATA MODEL:
[PASTE HERE]

API ENDPOINTS:
[PASTE HERE]

TECHNICAL ARCHITECTURE:
[PASTE HERE]

IMPLEMENTATION PHASE:

Do deep analysis of the proposed technical solution and write a report detailing the following:
# Technical Architecture Overview
# Scalability and Performance Analysis
# Security and Compliance Assessment
# Implementation Complexity Analysis
# Technology Stack Evaluation
# Pros and Cons from Technical Perspective
# Risk Assessment and Mitigation
# Alternative Technical Approaches
# Maintenance and Operational Considerations
# Cost and Resource Implications

The report should be in a single, downloadable file using markdown formatting.

VERIFICATION AND COMPLETION PHASE:

- Make sure the analysis covers all technical aspects
- Highlight any technical risks or concerns
- Suggest improvements where possible
- Include recommendations for implementation phases
```

## 7. Combined Technical Requirements

This is the final phase where we generate the combined technical requirements document. Use the most advanced reasoning model possible to create a detailed technical requirements document for the coding tools to implement.

Use the following prompt to create the combined technical requirements:

```
ANALYSIS PHASE:

Read each of the following technical documents and analyze them:

DATA MODEL:
[PASTE HERE]

API ENDPOINTS:
[PASTE HERE]

TECHNICAL ARCHITECTURE:
[PASTE HERE]

Confirm you have read the content of the documents, then continue...

IMPLEMENTATION PHASE:

Create a detailed technical requirements document that breaks down the implementation by technical component. The end result should be a list of technical features, with detailed backend implementation stories for each component.

Each technical story format should be in the following format:
- Story title
- Designate as backend API, database, infrastructure, or integration story
- Technical story in "As a developer, I need [technical requirement], so that [system capability]" format
- Technical implementation details
- Testable technical acceptance criteria
- Detailed Architecture Design Notes
- Database schema requirements (if applicable)
- API contract specifications (if applicable)
- Security and performance considerations
- Dependencies on other technical stories
- Related technical components for context

You should also provide overarching technical context in each feature description.

At the top of the document include:
- Complete data model for reference
- Technology stack specifications
- Infrastructure requirements
- Security and compliance requirements

Do NOT include any functional user stories - focus only on technical implementation requirements.
Do NOT add any functionality that isn't defined in the specifications above.

Include a 'Technical Context' section at the top that details the technical approach and architectural decisions.

VERIFICATION AND COMPLETION PHASE:
Validate your work to check that all technical components defined in the documents above meet all necessary requirements and there is no ambiguity or technical gaps before writing the final output.
```

## 8. Ensuring Technical Specification Precision

Dedicate substantial time and team effort to refining the technical specifications to eliminate vagueness and potential misinterpretations.

- Ensure all technical aspects are reviewed collaboratively by the development team.
- Revise any unclear sections to ensure the specifications are unambiguous.
- Validate that all technical requirements are implementable with the chosen technology stack.
- Ensure security, performance, and scalability requirements are properly addressed.

## 10. Saving Technical Specifications

Once you have the markdown text, save it in the folder that was set up at the start of the project in `technical-specification.md` format. It's important that this file is INSIDE the code repository, as we will have the AI-powered IDE reference it later in the workflow.

## Next Steps

Once your technical specification is complete, you can proceed with the development phase where both the [Functional Requirements](01-functional-requirement.md) and Technical Specification will be used together to guide the AI-powered code generation process.

## Related Resources

- [Development](03-development.md) - Next step in the workflow for implementing your specifications
- [Testing](04-testing.md) - Comprehensive testing strategies for your implementation
- [Prompt Library](../../prompt-library/README.md) - Ready-to-use prompts for technical specification tasks
- [Glossary](../../glossary.md) - Key terms and definitions used in this workflow 