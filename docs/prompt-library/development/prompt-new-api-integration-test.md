---
description: Template for creating comprehensive API integration tests covering various scenarios and edge cases.
---

# New API Integration Test Prompt

```
Create integrations tests for [feature] in [file path].

## Context
- Feature location: [file path]
- Related services/dependencies: [repo, service]

## Analysis Requirements
1. Review testing standards from the testing cursor rules
2. Study existing integration tests for patterns and conventions
3. Analyze:
   - Source code architecture
   - Integration points
   - External dependencies requiring mocks
   - Data models and flows
   - Existing test coverage

## Implementation Guidelines
1. Test Structure:
   - Use Given-When-Then pattern with descriptive comments
   - Focus on end-to-end workflows over isolated units
   - Mock external dependencies appropriately

2. Test Coverage:
   - Core user scenarios and workflows
   - Edge cases and error conditions
   - Both happy and unhappy paths

3. Quality Standards:
   - Clear test descriptions
   - Meaningful assertions
   - Efficient test setup and teardown
   - Appropriate use of test utilities and helpers @conftest.py
   - Follow the project's test data management pattern in @test_data.py
   - Do not define test data directly in test files

## Constraints
- Scope: Modify only the test file and test utilities / helpers
- Format: Deliver complete, production-ready test code
- Standards: Follow project's established testing patterns
- Dependencies: Use existing test utilities and helpers

## Output
Provide the complete test implementation in a single code block, following all project conventions and testing standards. 