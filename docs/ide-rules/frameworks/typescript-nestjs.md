# TypeScript coding standards and type safety guidelines

To create a new Cursor Rule:

1. Enter the name as `typescript-nestjs`
2. Copy & paste the file content from below

For more information, visit the [Project rules](https://docs.cursor.com/context/rules#project-rules).


```markdown
---
description: TypeScript coding standards and type safety guidelines
globs: **/*.ts, src/**/*.ts
alwaysApply: false
---

# TypeScript coding standards and type safety guidelines

- Use strict null checks to prevent null or undefined errors
- Prefer interfaces over types for better extensibility
- Utilize type guards and assertions for runtime type checking
- Implement proper type inference to reduce unnecessary type annotations
- Avoid using the `any` type; instead, create specific types or use `unknown`
- Use readonly properties and the `as const` assertion for immutability

## NestJS Best practices

- Organize your application using a modular architecture
- Encapsulate API logic within modules, one per main domain/route
- Use DTOs with class-validator for input validation
- Implement services for business logic and data persistence
- Utilize MikroORM for database operations and entity management
- Create a core module for global filters, middlewares, guards, and interceptors
- Develop a shared module for utilities and services used across multiple modules
- Follow SOLID principles, favoring composition over inheritance
- Use NestJS's built-in exception filters for error handling
- Implement proper dependency injection to enhance testability

## Testing with Jest best practices 

- Follow the Arrange-Act-Assert pattern in your test cases
- Write unit tests for each public function or method
- Use test doubles (mocks, stubs, spies) to isolate dependencies
- Implement end-to-end tests for each API module
- Add a smoke test endpoint (e.g., `/admin/test`) to each controller
- Name test variables clearly using conventions like `inputX`, `mockX`, `actualX`, `expectedX`
- Utilize Jest's snapshot testing for UI components and complex data structures
- Use Jest's code coverage reports to ensure adequate test coverage

## Class-validator best practices

- Use DTOs to define the structure of incoming data
- Implement custom validators for complex validation logic
- Utilize the `@IsOptional()` decorator for optional fields
- Use the `@ValidateNested()` decorator for validating nested objects
- Implement conditional validation using the `@ValidateIf()` decorator
- Use the `ValidationPipe` in NestJS for automatic DTO validation
- Leverage the `ValidationError` class for detailed error reporting
```