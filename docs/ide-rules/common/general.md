---
description: Universal project guidelines and coding principles that apply across all languages and frameworks for maintaining consistent code quality.
---

# General Project Guidelines

## IDE Configuration Headers

### For Cursor IDE

To create a new Cursor Rule:

1. Create a file named `general.md` in `.cursor/rules/`
2. Copy & paste the following header and rule content below:

```markdown
---
description: General Project Guidelines
globs: **/*
alwaysApply: true
---
```

### For Kiro IDE

To create a new Kiro Steering Document:

1. Create a file named `general.md` in `.kiro/steering/`
2. Copy & paste the following header and rule content below:

```markdown
---
inclusion: always
---
```

For more information about IDE rules, visit:
- [Cursor Project Rules](https://docs.cursor.com/context/rules#project-rules)
- [Kiro Steering Documents](https://github.com/kirolabs/kiro)

## Rule Content

```markdown
# General Project Guidelines

## Technical Stack
- <React>
- Dependency management: <npm>
- Hosted on <Gitlab>
  - URL: <https://gitlab.com/owner/repo>
  - Name: <Name>
  - ID: <00000000>
- Automated build and deployment with <GitLab CI>

## Code Style
- Keep code concise and readable. Prefer simple, readable implementation over premature optimization.
- Use meaningful variable and function names  
- Add appropriate comments to explain complex logic  
- Follow the official style guides of each programming language  

## Project Structure
- Keep the project structure clear and follow modular principles  
- Place related functions in the same directory  
- Use appropriate directory names that reflect the content  

## General Development Principles
- Write testable code  
- Avoid duplicated code (DRY principle)  
- Prefer mature tools over reinventing the wheel  
- Consider code maintainability and scalability  

## Response Language
- Always respond to users in English
```

