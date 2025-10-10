# Generate Unit Tests

Create comprehensive unit tests for the current file or selected code.

## Objective

Generate high-quality unit tests that achieve good code coverage and test all critical paths and edge cases.

## Requirements

- Use the project's testing framework (Jest, Vitest, etc.)
- Follow the project's testing patterns and conventions
- Include positive test cases (happy path)
- Include negative test cases (error conditions)
- Test edge cases and boundary conditions
- Mock external dependencies appropriately
- Use descriptive test names that explain what is being tested
- Organize tests in logical describe blocks

## Test Coverage Goals

- Aim for >80% code coverage
- Test all public methods/functions
- Test error handling
- Test with various input types
- Test async operations properly

## Output

Generate a complete test file with:
- Proper imports and setup
- beforeEach/afterEach hooks if needed
- Well-organized test suites
- Clear assertions
- Helpful comments for complex scenarios
