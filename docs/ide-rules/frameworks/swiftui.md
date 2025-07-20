# SwiftUI Rules

To create a new Cursor Rule:

1. Enter the name as `swiftui`
2. Copy & paste the file content from below

For more information, visit the [Project rules](https://docs.cursor.com/context/rules#project-rules).


```markdown
---
description: SwiftUI Rules
globs: **/*.swift
alwaysApply: false
---


# SwiftUI Rules

- Use structs to create views and keep them small and focused
- Use @State to manage simple view local state
- Use @ObservableObject with @Published to manage shared state
- Use @Binding to pass mutable state to child views
- Create custom ViewModifiers to implement reusable styles
- Use environment objects for dependency injection
- Use LazyVStack and LazyHStack for large collections
- Extract complex view logic into separate components
```