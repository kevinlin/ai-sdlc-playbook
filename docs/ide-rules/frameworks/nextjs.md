# Next.js Best Practices

## IDE Configuration Headers

### For Cursor IDE

To create a new Cursor Rule:

1. Enter the name as `nextjs`
2. Copy & paste the following header and rule content below:

```markdown
---
description: Next.js Best Practices
globs: **/*.jsx, **/*.tsx, pages/**/*
alwaysApply: false
---
```

### For Kiro IDE

To create a new Kiro Steering Document:

1. Create a file named `nextjs.md` in `.kiro/steering/`
2. Copy & paste the following header and rule content below:

```markdown
---
inclusion: fileMatch
fileMatchPattern: '**/*.jsx,**/*.tsx,pages/**/*'
---
```

For more information about IDE rules, visit:
- [Cursor Project Rules](https://docs.cursor.com/context/rules#project-rules)
- [Kiro Steering Documents](https://github.com/kirolabs/kiro)

## Rule Content

