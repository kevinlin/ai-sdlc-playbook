# Documentation Guidelines

## IDE Configuration Headers

### For Cursor IDE

To create a new Cursor Rule:

1. Enter the name as `document`
2. Copy & paste the following header and rule content below:

```markdown
---
description: Documentation Guidelines
globs: **/*.md, **/*.txt
alwaysApply: false
---
```

### For Kiro IDE

To create a new Kiro Steering Document:

1. Create a file named `documentation.md` in `.kiro/steering/`
2. Copy & paste the following header and rule content below:

```markdown
---
inclusion: fileMatch
fileMatchPattern: '**/*.md,**/*.txt'
---
```

For more information about IDE rules, visit:
- [Cursor Project Rules](https://docs.cursor.com/context/rules#project-rules)
- [Kiro Steering Documents](https://github.com/kirolabs/kiro)

## Rule Content

```markdown
# Documentation Guidelines

## General Requirements
- All documentation should use Markdown format
- Use concise and clear language
- Documentation content should be kept up to date
- Avoid spelling and grammatical errors
- Use English as the primary language

## Directory Structure
- `README.md`: Project root, provides project overview
- `docs/`: Stores detailed documentation
  - `guide/`: User guides
  - `api/`: API documentation
  - `examples/`: Example code documentation

## README.md Content Guidelines
- Project name and brief description
- Tech stack description
- Project structure description
- Usage instructions
- License information

## Version Record Guidelines
- Use `CHANGELOG.md` to record version changes
- Follow Semantic Versioning guidelines
- Each version should include: new features, bug fixes, breaking changes

## Documentation Content Organization
- From general to specific, from simple to complex
- Place important information at the beginning
- Related content should be grouped together
- Use subheadings and lists to enhance readability
- Avoid overly long paragraphs, keep content concise

## Code Example Guidelines
- Provide complete and runnable examples
- Code should be concise and easy to understand
- Add appropriate comments to explain key parts
- Explain the expected output or behavior of the code
- Update examples to match the latest API
```