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

### Headings
- Use ATX style headings (use # symbol)
- Heading levels should not be skipped (e.g., do not use h3 directly after h1)
- Use sentence case for headings (capitalize only the first word and proper nouns)

### Code Blocks
- Code blocks should specify the language type for syntax highlighting
- Use triple backticks (```) for multi-line code blocks
- Use single backticks (`) for inline code

### Lists
- List items should use `-` instead of `*` or `+` for consistency
- Include a new line before lists when they follow paragraphs or other content blocks
- Lists that immediately follow headings or other lists don't require additional spacing
- Use consistent indentation (4 spaces) for nested list items
- For numbered lists, use `1.` for all items (markdown will auto-number)

#### Nested List Spacing
- Always include a new line before nested sub-lists (lists with indentation)
- This applies when transitioning from a parent list item to its sub-items
- Example of correct nested list formatting:
  ```markdown
  - Parent item with description
  
    - Sub-item 1
    - Sub-item 2
  ```
- Exception: Immediate continuation lists (same level) don't need extra spacing

#### List Structure Examples
**Correct - with new line before sub-list:**
```markdown
- Support four rule types:

  - **Always**: Always included in the model context
  - **Auto Attached**: Included when files matching a glob pattern
```

**Incorrect - missing new line before sub-list:**
```markdown
- Support four rule types:
  - **Always**: Always included in the model context
  - **Auto Attached**: Included when files matching a glob pattern
```

### Links and References
- Use `[text](URL)` format for external links
- Use `[text](mdc:URL)` format for internal project references
- Provide descriptive link text (avoid "click here" or bare URLs)
- Use reference-style links `[text][ref]` for repeated or long URLs

### Images
- Use `![alt text](imageURL)` format
- Always provide meaningful alt text for accessibility
- Use `![alt text](mdc:imageURL)` for internal project images

### Spacing and Structure
- Use one blank line between different content sections
- Use two blank lines before major headings (H1, H2) when following content
- No trailing whitespace at the end of lines
- End files with a single newline

## Content Guidelines

### Charts and Diagrams
- Use clear, high-resolution images
- Charts should be simple and avoid excessive decoration
- Consider accessibility for colorblind users when choosing colors
- Provide alternative text descriptions for complex diagrams

### Writing Style
- Use clear, concise language
- Write in active voice when possible
- Use consistent terminology throughout the document
- Break up long paragraphs for better readability
```