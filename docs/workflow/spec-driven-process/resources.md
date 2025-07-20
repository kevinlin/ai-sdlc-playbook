# Resources and References

Templates, tools, standards, and practical guidance for effective spec-driven development.

## Quick Reference Templates

### Micro Spec Template (< 1 day effort)
For simple bug fixes, configuration changes, or minor tweaks:

```markdown
# [Brief Description]

**What:** One sentence describing the change
**Why:** Brief justification
**How:** 2-3 bullet points of implementation steps
**Acceptance:** Simple pass/fail criteria

## Example
# Fix Login Button Color

**What:** Change login button from blue to green to match brand guidelines
**Why:** Brand consistency requirement from design team
**How:** 
- Update CSS variable `--primary-button-color` to `#28a745`
- Verify color meets accessibility contrast requirements
**Acceptance:** Login button displays green and passes WCAG AA contrast test
```

### Quick Spec Template (1-3 days effort)
For small features, API endpoints, or component modifications:

```markdown
# [Feature Name] - Quick Spec

## Requirements
**As a** [user type]
**I want** [capability]
**So that** [benefit]

**Acceptance Criteria:**
- [ ] [Specific, testable criterion]
- [ ] [Another criterion]

## Implementation Tasks
1. [Specific coding task with estimated time]
2. [Another task]
3. [Testing/validation task]

## Definition of Done
- [ ] Code complete and reviewed
- [ ] Tests passing
- [ ] Acceptance criteria verified
```

### Full Requirements Template
For complex features requiring comprehensive specification:

```markdown
# Requirements Document

## Introduction
[Brief overview of the feature and its purpose]

## Requirements

### Requirement 1: [Title]
**User Story:** As a [role], I want [functionality], so that [benefit]

#### Acceptance Criteria
1. WHEN [event] THEN [system] SHALL [response]
2. IF [condition] THEN [system] SHALL [behavior]
3. WHEN [event] AND [condition] THEN [system] SHALL [response]

#### Additional Details
- **Priority**: [High/Medium/Low]
- **Complexity**: [High/Medium/Low]
- **Dependencies**: [List dependencies]
- **Assumptions**: [List assumptions]

### Requirement 2: [Title]
[Continue with additional requirements...]

## Non-Functional Requirements
- **Performance**: [Specific performance criteria]
- **Security**: [Security requirements]
- **Accessibility**: [Accessibility standards]
- **Browser Support**: [Supported browsers/versions]
```

### Design Template
For technical architecture and component design:

```markdown
# Design Document

## Architecture Overview
[High-level description of system approach]

## System Components

### Component 1: [Name]
- **Purpose**: [What it does]
- **Key Functions**: [Main functionality]
- **Interfaces**: [How it connects to other parts]
- **Data**: [Key data structures]

## API Design

### Endpoint 1: [Name]
- **Method**: GET/POST/PUT/DELETE
- **Path**: /api/path
- **Request**: [Format and parameters]
- **Response**: [Expected response format]
- **Errors**: [Error handling]

## Data Models
[Define key data structures and relationships]

## Testing Strategy
[How the design will be tested]

## Error Handling
[How errors are managed throughout the system]
```

### Tasks Template
For breaking down implementation work:

```markdown
# Tasks Document

## Implementation Plan

### 1. [Major Component]
- [ ] 1.1 [Specific implementation task]
  - [Implementation details]
  - [Files/components to create]
  - _Requirements: [Requirement references]_
- [ ] 1.2 [Next specific task]
  - [Task details]

### 2. [Next Major Component]
- [ ] 2.1 [Specific implementation task]
  - [Task details]

## Task Dependencies
[Description of task ordering and dependencies]

## Validation Strategy
[How to verify each task is complete]
```

## EARS Standards Reference

EARS (Easy Approach to Requirements Syntax) provides structured language for writing clear, testable requirements.

### EARS Keywords

**WHEN** (Event-driven requirements)
- Format: `WHEN [event/trigger] THEN [system] SHALL [response]`
- Example: `WHEN user clicks "Save" button THEN system SHALL validate all form fields`

**IF** (State-driven requirements)
- Format: `IF [condition] THEN [system] SHALL [response]`
- Example: `IF user is not authenticated THEN system SHALL deny access to protected resources`

**WHILE** (Continuous requirements)
- Format: `WHILE [condition] [system] SHALL [continuous behavior]`
- Example: `WHILE file is uploading system SHALL display progress indicator`

**WHERE** (Optional/contextual requirements)
- Format: `WHERE [location/context] [system] SHALL [behavior]`
- Example: `WHERE user is on mobile device system SHALL use responsive layout`

### EARS Best Practices

1. **Use Active Voice**: Write requirements using active voice for clarity
2. **Be Specific**: Avoid vague terms like "user-friendly" or "fast"
3. **One Requirement Per Statement**: Each EARS statement should contain exactly one requirement
4. **Testable Outcomes**: Every requirement should be verifiable through testing
5. **Consistent Terminology**: Use the same terms throughout all requirements

### EARS Anti-Patterns

- **Compound Requirements**: Avoid multiple SHALL statements in one requirement
- **Vague Conditions**: Don't use unclear triggers like "when appropriate"
- **Implementation Details**: Focus on what, not how
- **Untestable Requirements**: Avoid subjective terms that can't be measured

## AI Collaboration Best Practices

### Core Principles

1. **Provide Rich Context**: Include background about your project, technology stack, and constraints
2. **Be Specific and Concrete**: Use specific scenarios rather than abstract descriptions
3. **Structure Complex Requests**: Break down large features into logical phases
4. **Iterate Gradually**: Build complexity through multiple interactions
5. **Validate Output**: Review and refine AI-generated content

### Effective Prompting Strategies

#### Requirements Phase
```
"Based on this feature idea: [description], help me identify all the user stories 
and acceptance criteria using EARS format. Consider edge cases and error scenarios."

"Review these requirements and identify any gaps, ambiguities, or missing 
scenarios: [requirements text]"
```

#### Design Phase
```
"Given these requirements: [requirements], help me design a system architecture. 
Consider scalability, maintainability, and integration requirements."

"I need to design an API for [functionality]. Based on these requirements, 
what endpoints, request/response formats, and error handling should I include?"
```

#### Tasks Phase
```
"Break down this design into specific implementation tasks. Order them for 
incremental development and early validation: [design]"

"Convert this component design into coding tasks with clear objectives and 
completion criteria: [component description]"
```

### Common Pitfalls and Solutions

**Problem**: AI generates generic or irrelevant content
**Solution**: Provide more specific context and constraints

**Problem**: AI misunderstands requirements
**Solution**: Break requests into smaller, focused questions

**Problem**: AI suggests overly complex solutions
**Solution**: Ask for simpler alternatives and explain constraints

**Problem**: Inconsistent output across interactions
**Solution**: Provide previous context and maintain conversation history

### Best Practices by Situation

**Do:**
- Provide complete context and background
- Ask for explanations of reasoning
- Request multiple options when appropriate
- Validate AI suggestions against requirements
- Use AI to identify potential issues or gaps

**Don't:**
- Accept AI output without review
- Skip validation steps
- Rely on AI for subjective business decisions
- Let AI make architectural decisions without input
- Assume AI understands implicit requirements

## Recommended Tools

### Documentation Tools
- **Markdown Editors**: Typora, Mark Text, or VS Code with Markdown extensions
- **Diagramming**: Mermaid for simple diagrams, Lucidchart for complex architectures
- **Collaboration**: Notion, Confluence, or GitHub wikis for team documentation

### Development Tools
- **API Design**: Postman, Insomnia, or OpenAPI/Swagger for API specification
- **Database Design**: DBDiagram, QuickDBD for schema visualization
- **Project Management**: Linear, Jira, or GitHub Issues for task tracking

### AI Collaboration Tools
- **Code Assistants**: GitHub Copilot, Cursor, or Claude for implementation help
- **Documentation**: Use AI for initial drafts, then refine based on specific context
- **Design Review**: AI can help identify missing cases or architectural issues

## Validation Checklists

### Requirements Quality Checklist
- [ ] Each requirement is testable and measurable
- [ ] Requirements cover normal, edge, and error cases
- [ ] User stories provide clear business value
- [ ] Acceptance criteria are specific and unambiguous
- [ ] Requirements are independent and don't conflict
- [ ] All user roles and interactions are addressed

### Design Quality Checklist
- [ ] Design addresses all requirements
- [ ] Components are well-defined with clear responsibilities
- [ ] APIs are complete and consistent
- [ ] Data models support all required operations
- [ ] Error handling is comprehensive
- [ ] Testing approach is defined

### Task Quality Checklist
- [ ] Tasks are specific and actionable
- [ ] Each task produces testable code
- [ ] Dependencies are clear and logical
- [ ] Requirements are traceable to tasks
- [ ] Implementation can proceed incrementally

## Integration with Development Workflows

### Agile/Scrum Integration
- Use specs for larger user stories or epics
- Create specs during sprint planning
- Reference specs during daily standups and reviews
- Update specs based on sprint retrospective feedback

### Code Review Process
- Include spec review as part of code review
- Verify implementation follows spec design
- Update specs when implementation reveals better approaches
- Use specs to provide context for reviewers

### Continuous Integration
- Include spec validation in CI pipeline
- Ensure implementation matches spec requirements
- Use specs for automated testing guidance
- Update specs as part of the development process

## Adapting to Different Project Types

### Startup/MVP Projects
- Focus on core user value
- Use lightweight specs for rapid iteration
- Prioritize working software over comprehensive documentation
- Plan for future expansion but don't over-engineer

### Enterprise Projects
- Comprehensive documentation requirements
- Stakeholder approval processes
- Compliance and security considerations
- Long-term maintenance and knowledge preservation

### Open Source Projects
- Clear contributor guidelines
- Public documentation standards
- Community collaboration considerations
- Backwards compatibility requirements

### Legacy System Integration
- Existing system constraints
- Migration planning considerations
- Risk mitigation strategies
- Gradual replacement approaches 