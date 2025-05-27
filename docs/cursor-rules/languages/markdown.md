# Markdown Guidelines

To create a new Cursor Rule:

1. Enter the name as `markdown`
2. Copy & paste the file content from below

For more information, visit the [Project rules](https://docs.cursor.com/context/rules#project-rules).


```markdown
---
description: Documentation Guidelines
globs: **/*.md, **/*.mdc
alwaysApply: false
---

# Markdown Guidelines

## Markdown Formatting Guidelines
- Use ATX style headings (use # symbol)
- Heading levels should not be skipped (e.g., do not use h3 directly after h1)
- Code blocks should specify the language type
- List items should use - instead of * or +
- Links should use [text](mdc:URL) format
- Images should use ![alt text](mdc:imageURL) format

## Charts and Images
- Use clear, high-resolution images
- Provide meaningful alt text for images
- Charts should be simple, avoid excessive decoration
- Chart colors should consider accessibility for colorblind users
```