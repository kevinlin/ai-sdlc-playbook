---
description: DrawIO diagram creation guidelines for technical documentation and system architecture visualization.
---

# Draw.io Diagram Drawing Guide

## IDE Configuration Headers

### For Cursor IDE

To create a new Cursor Rule:

1. Enter the name as `drawio`
2. Copy & paste the following header and rule content below:

```
---
description: Draw.io Diagram Drawing Guide
globs: **/*.drawio
alwaysApply: false
---
```

### For Kiro IDE

To create a new Kiro Steering Document:

1. Create a file named `drawio.md` in `.kiro/steering/`
2. Copy & paste the following header and rule content below:

```
---
inclusion: fileMatch
fileMatchPattern: '**/*.drawio'
---
```

For more information about IDE rules, visit:
- [Cursor Project Rules](https://docs.cursor.com/context/rules#project-rules)
- [Kiro Steering Documents](https://github.com/kirolabs/kiro)

## Rule Content


~~~markdown
# Draw.io Diagram Drawing Guide

## Basic Conventions

### File Naming
- Format: `[module]_[diagram type]_[version].drawio`
- Example: `ai_assistant_architecture_v1.drawio`

### Component Color Standards
- **AI/LLM components**: light blue fill `#dae8fc` + blue border `#6c8ebf`
- **Knowledge base / data**: light yellow fill `#fff2cc` + yellow border `#d6b656`
- **Platform services**: light grey fill `#f5f5f5` + grey border `#666666`
- **External / user**: white fill + black border
- **Connector lines**: black solid line; use thicker line (`strokeWidth=2`) for critical flows

### Shapes and Styles
- **Standard component**: rounded rectangle with shadow
- **Section/group container**: large rounded rectangle with light background
- **Connectors**: orthogonal connectors; avoid arrow overlaps
- **Annotations/notes**: concise Chinese text; **bold** key information

## Drawing Principles

1. **Layered layout**: strictly left‑to‑right (client → server → AI service → external systems)
2. **Group core components**: cluster user‑interaction related components and label module titles
3. **Clear flow breaks**: solid lines for main flow; dashed lines for responses/exceptions
4. **Alignment**: horizontally align components in the same layer; connectors stay orthogonal

## Standard Architecture Template

### AI System Architecture Layout
```
[Client]      [Server]      [AI Service]     [AI Engine]
   |             |               |              |
UI  →  Business  →  AI API  →  LLM Model
   |             |               |
   └→ Routing → Agent → Knowledge Base
```

### Component Dimensions
- **Core blocks**: width 550 px, height 270 px, light grey background
- **Standard components**: width 120 px, height 60 px, with shadow
- **Connectors**: `strokeWidth=2`, Orthogonal style
- **Label position**: above or beside the connector; avoid overlap

### Flow Line Rules
- **Main flow**: black solid line, forward arrow
- **Return flow**: black dashed line, reverse arrow
- **Data flow**: bold solid line (`strokeWidth=2`)
- **Exception calls**: dashed line (`dashed=1`)
- **Arrow overlap**: adjust start/end points; use different paths
- **Line spacing**: keep solid and dashed lines on separate paths, at least 20 px apart

---

## Version Control

### Versioned File Names
- Format: `[module]_[diagram type]_v[version]_[YYYYMMDD].drawio`
- Example: `aiconf_system_flow_v1.1_20250619.drawio`
- Version rules:
  - **v1.0**: initial release
  - **v1.1**: minor changes (component tweaks, style optimisations)
  - **v2.0**: major changes (architecture updates, module refactor)

### Standard Workflow

1. **Create a copy of the original file**
   ```bash
   cp <original>.drawio <original>_v<new-version>_<YYYYMMDD>.drawio
   ```
   Example:
   ```bash
   cp aiconf_system_flow_v1.0_20250619.drawio \
      aiconf_system_flow_v1.1_20250619.drawio
   ```

2. **Edit the copy**  
   Make all required changes in the new file.

3. **Verify completion**
   - Check that all requirements are met.
   - Ensure the diagram opens and renders correctly.
   - Confirm the new version follows these standards.

4. **Update the master file**
   ```bash
   cp <copy>.drawio <master>.drawio
   ```

5. **Update the CHANGELOG**  
   Record the new version in `CHANGELOG.md`.

### Changelog Format
```markdown
## [version] - YYYY‑MM‑DD

### Added
- <file>: brief description of the feature

### Fixed
- <file>: brief description of the issue fixed

### Technical Details
- Key technical implementation points
```

### Example Workflow
```bash
# 1. Copy the original file
cp aiconf_system_flow_v1.0_20250619.drawio \
   aiconf_system_flow_v1.1_20250619.drawio

# 2. Edit the copy
#   (open aiconf_system_flow_v1.1_20250619.drawio)

# 3. Update CHANGELOG.md
# ## [v1.1] - 2025-06-19
# ### Fixed
# - <description of the fix>
```

### Best Practices
- **Copy then edit**: always modify the copy, never the original
- **Incremental checks**: validate against requirements after each change
- **Concise log**: record only key changes in the CHANGELOG
- **Keep history**: keep old versions; build a version trail
~~~