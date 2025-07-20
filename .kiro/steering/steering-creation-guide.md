---
inclusion: manual
---

# Steering Document Creation and Usage Guide

## What Are Steering Documents?

Steering documents are contextual guidelines that influence how I approach development tasks. They contain project-specific standards, conventions, and best practices that help me provide more relevant and consistent assistance.

## How Steering Documents Work

### Inclusion Mechanisms
1. **Always Included (Default)**: Documents without front-matter are included in every interaction
2. **File Match Conditional**: Documents with `inclusion: fileMatch` and `fileMatchPattern` are included when specific files are in context
3. **Manual Inclusion**: Documents with `inclusion: manual` are only included when explicitly referenced with `#steering-name`

### Context Integration
- Steering content is injected into my system context before processing user requests
- I receive the full content of applicable steering documents
- Multiple steering documents can be active simultaneously
- File references using `#[[file:path]]` syntax are resolved and included

## What Goes Into Steering Documents

### Core Categories I Create:

1. **Development Environment Standards**
   - Local setup procedures
   - Tool configurations
   - Environment variable management
   - Build and deployment processes

2. **Code Quality Guidelines**
   - Language-specific style guides
   - Naming conventions
   - Code organization patterns
   - Documentation requirements

3. **Git Workflow Standards**
   - Branch naming conventions
   - Commit message formats
   - Pull request processes
   - Code review guidelines

4. **Technology-Specific Standards**
   - Frontend development patterns
   - Backend API design
   - Database management
   - Testing strategies

5. **Security and Performance**
   - Security best practices
   - Performance optimization guidelines
   - Monitoring and alerting standards

### Content Structure I Follow:

```markdown
---
inclusion: [always|fileMatch|manual]
fileMatchPattern: 'pattern' # if fileMatch
---

# Clear Title

## Organized Sections
- Specific, actionable guidelines
- Code examples where relevant
- Tool configurations
- Reference to external files using #[[file:path]]

## Implementation Details
- Step-by-step procedures
- Common pitfalls to avoid
- Quality checkpoints
```

## How I Build Steering Documents

### Assessment Process:
1. **Project Analysis**: I examine the codebase structure, technologies used, and existing patterns
2. **Gap Identification**: I identify areas where standards would improve consistency
3. **Priority Ranking**: I focus on high-impact areas first (security, code quality, workflow)
4. **Template Selection**: I choose appropriate templates based on project type

### Content Development:
1. **Research Best Practices**: I draw from industry standards and proven patterns
2. **Contextualize for Project**: I adapt generic practices to specific project needs
3. **Include Examples**: I provide concrete code examples and configurations
4. **Reference Integration**: I link to existing project files and specifications

### Quality Assurance:
1. **Completeness Check**: Ensure all critical areas are covered
2. **Consistency Validation**: Verify guidelines don't conflict with each other
3. **Practicality Assessment**: Confirm guidelines are actionable and realistic
4. **Update Mechanism**: Plan for maintaining documents as project evolves

## Inclusion Strategy and Context Transmission

### What Gets Sent:
- **Full Content**: Complete steering document content is transmitted
- **Resolved References**: Files referenced with `#[[file:path]]` are read and included
- **Multiple Documents**: All applicable steering documents are combined
- **Real-time Evaluation**: Inclusion rules are evaluated for each interaction

### When Documents Are Included:
- **Always**: Default behavior for documents without front-matter
- **File Context Triggers**: When specific file patterns are in the conversation context
- **Manual Triggers**: When user explicitly references with `#steering-name`
- **Automatic Resolution**: System determines relevance based on file patterns

### Context Limitations:
- Large steering documents may be truncated if they exceed context limits
- Priority is given to more specific/relevant steering documents
- Recent interactions may influence which documents are prioritized

## Best Practices for Steering Creation

### Do:
- Keep documents focused and specific
- Use clear, actionable language
- Include concrete examples
- Reference external specifications
- Update regularly as project evolves
- Use appropriate inclusion mechanisms

### Don't:
- Create overly broad or generic guidelines
- Duplicate information across multiple documents
- Include sensitive information or secrets
- Create conflicting standards
- Make documents too long or complex

## Maintenance and Evolution

### Regular Review:
- Assess effectiveness of existing steering documents
- Update based on project changes and learnings
- Remove outdated or conflicting guidelines
- Add new standards as project grows

### Feedback Integration:
- Monitor how well steering documents influence code quality
- Adjust based on team feedback and development patterns
- Refine inclusion patterns for better relevance
- Optimize document structure for clarity

## Technical Implementation Notes

### File Structure:
```
.kiro/steering/
├── project-standards.md (always included)
├── git-workflow.md (always included)
├── frontend-standards.md (fileMatch: *.tsx,*.jsx)
├── api-design.md (manual inclusion)
└── development-environment.md (fileMatch: package.json)
```

### Front-matter Options:
```yaml
---
inclusion: always|fileMatch|manual
fileMatchPattern: 'glob-pattern' # for fileMatch only
---
```

### File Reference Syntax:
```markdown
#[[file:relative/path/to/file.ext]]
```

This creates a comprehensive system for maintaining project consistency and providing contextual guidance throughout the development process.