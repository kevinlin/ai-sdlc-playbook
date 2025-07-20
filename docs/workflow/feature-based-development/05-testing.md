# 5. Testing

Testing effectively with AI can be challenging—often more so than developing new features. While AI can readily generate tests, these tests are not always valuable in the long term. We have observed that automated test creation without careful consideration often produces brittle, tightly coupled tests that break with code changes, offering little practical value.

This document outlines a recommended workflow for designing and implementing robust and sustainable tests utilising AI.

## Principles

1. **Test the Functionality, Not the Implementation**
    - Write tests that treat the service or endpoint as a "black box": supply known inputs and verify that the final responses, returned data, or side effects match the expected outcomes.  
    - Focus on overall functionality rather than internal method calls, keeping tests resilient to code changes.
2. **Prefer Integration Tests Over Isolated Unit Tests**
    - Integration tests simulate real-world usage and interactions between components, often revealing issues that isolated unit tests may miss.  
    - Reserve unit tests for discrete utility functions or algorithms that are sufficiently complex to warrant independent testing.
3. **Realistic Mocking of External Dependencies**
    - **Do mock:** Truly external systems such as databases, third-party APIs, and file systems—simulate realistic responses and error conditions.  
    - **Don't mock:** Internal modules, classes, or functions; test these together to ensure authentic interactions and comprehensive coverage.
4. **Adopt a Structured Test Design**
    - Utilise a clear narrative structure, such as the Given-When-Then format:
        - **Given:** Establish preconditions, test data, and necessary configurations.
        - **When:** Execute the core logic or function.
        - **Then:** Validate that the outcomes meet the specified expectations.
    - This approach emphasises outcomes over internal details and aids in maintaining clarity and consistency.
5. **Avoid Brittle Tests**
    - Refrain from hardcoding internal implementation details, such as specific function calls or class structures.  
    - Overreliance on internal details can lead to fragile tests that break with minor refactors.

## Integration Testing Workflow

The emphasis of the testing workflow is to have test-specific cursor rules and detailed prompts, along with close human interaction and review. 

### Prerequisites

- **Feature Requirements**: Ensure there is are detailed feature requirements with clear scope, as per the [Functional Requirements](01-functional-requirement.md). This could be a User Story or Product Requirement Document, in markdown format. The document should be accessible to the AI-powered IDE.
- **IDE Rules:** Ensure there are detailed [IDE rules for your chosen language](../../ide-rules/languages/README.md) to guide the AI tools in adhering to code style and design preferences.

### 1. Interactively Prompt the IDE

- Utilise an IDE in agentic mode to implement the tests.
- Use testing prompt templates based on your testing needs:
    - [Integration Test from Feature](../../prompt-library/development/prompt-new-integration-test-from-feature.md) - Comprehensive feature analysis and testing
    - [API Integration Test](../../prompt-library/development/prompt-new-api-integration-test.md) - API endpoint and service testing
    - [Frontend Integration Test](../../prompt-library/development/prompt-new-frontend-integration-test.md) - Frontend component and user interaction testing
- Reference your requirements file using the @file feature.
- As the AI generates the tests, monitor its plan to ensure alignment with your expectations.
- Once complete, "accept" the changes and review them in the git diff viewer. If the changes are unexpected or involve significant deletions, revert all changes, refine your prompt, and try again.

### 2. Run the Tests and Refine  

- Execute the tests.
- If issues arise, feed the results back into the chat to address them, providing sufficiently detailed prompting to guide the best course of action.

### 3. Review and Improve Test Coverage  

- If there are opportunities for enhanced test coverage, prompt the IDE with precise guidance and include the output from the test coverage report.
- Address improvements on a feature-by-feature or file-by-file basis.
- Avoid asking for improvements to the entire codebase coverage in a single prompt.

### 4. User Review  

- It is crucial that tests are thoroughly reviewed and understood.  
- Do not allow agents to generate tests unchecked; relying solely on them is akin to marking their own homework, which offers little practical value.

## End-to-End Testing Workflow

The workflow for end-to-end testing is similar to that for integration testing, with the key difference being that end-to-end tests are decoupled from the underlying code. This decoupling enables you to prompt the model to generate tests using only the requirements and rules, without referencing the source code.

Consequently, AI-generated end-to-end tests can be conducted either prior to code generation or independently by a dedicated QA team if desired.

Refer to the [prompt-new-e2e-test](../../prompt-library/development/prompt-new-e2e-test.md) for an example. 