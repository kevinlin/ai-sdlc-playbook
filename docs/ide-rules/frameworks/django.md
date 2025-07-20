# Django Best Practices

## IDE Configuration Headers

### For Cursor IDE

To create a new Cursor Rule:

1. Enter the name as `django`
2. Copy & paste the following header and rule content below:

```markdown
---
description: Django Best Practices
globs: **/*.py
alwaysApply: false
---
```

### For Kiro IDE

To create a new Kiro Steering Document:

1. Create a file named `django.md` in `.kiro/steering/`
2. Copy & paste the following header and rule content below:

```markdown
---
inclusion: fileMatch
fileMatchPattern: '**/*.py'
---
```

For more information about IDE rules, visit:
- [Cursor Project Rules](https://docs.cursor.com/context/rules#project-rules)
- [Kiro Steering Documents](https://github.com/kirolabs/kiro)

## Rule Content

