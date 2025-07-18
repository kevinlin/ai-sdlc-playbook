# Python Project Rules

To create a new Cursor Rule:

1. Enter the name as `general`
2. Copy & paste the file content from below

For more information, visit the [Project rules](https://docs.cursor.com/context/rules#project-rules).


```markdown
---
description: General Project Guidelines
globs: **/*
alwaysApply: false
---

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
- general.mdc: General guidelines (this file)
- python.mdc: Python development guidelines
- documentation.mdc: Documentation guidelines
- git.mdc: Git commit guidelines
```