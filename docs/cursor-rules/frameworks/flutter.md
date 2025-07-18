# Flutter Rules

To create a new Cursor Rule:

1. Enter the name as `flutter`
2. Copy & paste the file content from below

For more information, visit the [Project rules](https://docs.cursor.com/context/rules#project-rules).


```markdown
---
description: Flutter Rules
globs: **/*.dart
alwaysApply: false
---


# Flutter Rules

## Code style and structure
- Write concise and efficient source code.
- Strive for source code that is easy to read and maintain, and provide accurate examples.
- Avoid duplication of code: modularise widgets and functions into reusable components.
- Use descriptive variable names: use names with auxiliary verbs such as isLoading, hasError.

## Naming conventions
- Directories and files: use snakeCase (e.g. auth_wizard.dart).
- UpperCamelCase: use for class names/enumerations/typedefs/type parameters, etc.
- LowerCamelCase: used for variables/functions/class members (properties, methods), etc.
- lowercase_with_underscores (snakeCase): for files/directories/packages/libraries, etc.

## Import
- Place imports starting with dart: first (use lowercase_with_underscores for the import prefix).
- Next, import third-party packages (package:).
- Finally, import relative paths and files in the project.

## Dart Rules
- Use braces {} for all flow control structures (if, for, while, etc.).
- Use comment-outs proactively to help understand and maintain code.
- Use single quotes, avoid the use of double quotes and use consistent string literals to improve readability.
- Take advantage of type safety: use static typing in all code and utilise type inference wherever possible.

## UI and styling
- Use Material widgets.
- Unify theming: use ThemeData to apply consistent styles.

## Performance optimisation
- Prefer StatelessWidget when state is not required.
- Make use of const constructors: if widgets are immutable, use const to optimize builds.
```