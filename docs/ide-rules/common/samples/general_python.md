---
description: Sample Python project demonstrating general coding guidelines and best practices implementation.
---

# Python Project Rules

## IDE Configuration Headers

### For Cursor IDE

To create a new Cursor Rule:

1. Enter the name as `general`
2. Copy & paste the following header and rule content below:

```markdown
---
description: General Project Guidelines
globs: **/*
alwaysApply: false
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

## Tech Stack
- Python 3.10
- Poetry for dependency management
- GitHub Actions for automated build and deployment
- Use GitHub as the code hosting platform
- Use Bash scripts

## Code Style
- Keep code simple and readable
- Use meaningful variable and function names
- Add appropriate comments to explain complex logic
- Follow the official style guide for each language

## Project Structure
- Keep the project structure clear, following modular principles
- Related features should be placed in the same directory
- Use appropriate directory names that reflect their contents

## General Development Principles
- Write testable code
- Avoid duplicate code (DRY principle)
- Prefer existing libraries and tools, avoid reinventing the wheel
- Consider code maintainability and scalability

## Response Language
- Always reply to users in English

## Rule File Description
This project uses the following rule files:
- general: General guidelines (this file)
- python: Python development guidelines
- documentation: Documentation guidelines
- git: Git commit guidelines
```