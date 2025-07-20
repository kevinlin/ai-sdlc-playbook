# Spec-Driven Development Guide

Complete guide to transforming ideas into implementable features through systematic specification.

## Table of Contents

1. [Understanding Spec-Driven Development](#understanding-spec-driven-development)
2. [When and How to Use Specs](#when-and-how-to-use-specs)
3. [Phase 1: Requirements](#phase-1-requirements)
4. [Phase 2: Design](#phase-2-design)
5. [Phase 3: Tasks](#phase-3-tasks)
6. [Implementation and Execution](#implementation-and-execution)
7. [Working with AI](#working-with-ai)

---

## Understanding Spec-Driven Development

### Core Philosophy

Spec-driven development is built on the principle of **clarity before code**. By investing time in understanding requirements, designing solutions, and planning implementation, we reduce uncertainty, minimize rework, and increase the likelihood of building the right thing correctly.

### Key Characteristics

- **Structured Planning**: Features developed through a deliberate three-phase process
- **Living Documentation**: Specifications evolve and serve as ongoing communication tools
- **AI-Optimized**: Provides structured context that AI tools need to be most effective
- **Quality-Focused**: Emphasizes building the right thing correctly from the start
- **Collaborative**: Facilitates clear communication among team members and stakeholders

### The Three-Phase Arc

```
Idea → Requirements → Design → Tasks → Implementation
```

1. **Requirements**: Transform vague ideas into clear, testable requirements
2. **Design**: Create comprehensive technical plans for implementation
3. **Tasks**: Break down designs into actionable, sequential implementation steps

Each phase builds upon the previous one, with explicit validation to ensure quality and alignment before proceeding.

---

## When and How to Use Specs

### Decision Framework

Use this framework to determine the right level of specification:

#### Full Spec Process (Requirements → Design → Tasks)

**✅ Use when:**
- Features involve multiple components or integrations
- Working on high-stakes projects where failure is costly
- Coordinating work across multiple developers or teams
- Documentation and knowledge preservation are critical
- Requirements are complex or likely to change

#### Lightweight Spec Process (Requirements + Tasks Only)

**⚡ Use when:**
- Feature is moderately complex but well-understood
- Working with familiar technology patterns
- Time constraints require faster delivery
- Team is small and communication is easy

#### Micro Spec Process (Brief Documentation Only)

**📝 Use when:**
- Simple changes taking less than 1 day
- Bug fixes or minor adjustments
- Configuration updates or copy changes

#### Skip Specs Entirely

**❌ Skip when:**
- Making simple bug fixes or minor tweaks
- Building experimental prototypes for learning
- Handling time-critical hotfixes
- Working alone on personal projects

### Complexity Assessment Questions

- How many moving parts are involved?
- What's the cost of getting it wrong?
- How many people need to understand the work?
- How much time do you have for planning?
- How well-understood is the problem domain?

---

## Phase 1: Requirements

Transform rough feature ideas into clear, testable requirements using structured formats.

### Purpose

The requirements phase serves to:
- Transform vague feature ideas into concrete, measurable requirements
- Establish clear acceptance criteria for feature success
- Create shared understanding between stakeholders
- Provide foundation for design and implementation decisions

### Process Overview

```
Feature Idea → User Stories → Acceptance Criteria → Validation → Approved Requirements
```

### Step 1: Generate User Stories

Start with user-centered stories that express value and purpose:

**Format:**
```
As a [role/user type], I want [desired functionality], so that [benefit/value]
```

**Guidelines:**
- Focus on what the user experiences, not technical implementation
- Consider all user roles that interact with the feature
- Think about the complete user journey
- Include edge cases and error scenarios

### Step 2: Write Acceptance Criteria

Use EARS (Easy Approach to Requirements Syntax) format for clear, testable criteria:

**EARS Keywords:**
- **WHEN**: Describes triggering events or conditions
- **IF**: Describes preconditions that must be met
- **THEN**: Describes the system's required response
- **SHALL**: Indicates mandatory behavior (use consistently)
- **AND/OR**: Combines conditions when necessary

**Example:**
```
WHEN user submits valid login credentials THEN system SHALL authenticate user and redirect to dashboard
IF user enters invalid password three times THEN system SHALL lock account for 15 minutes
WHEN user is logged in AND session expires THEN system SHALL redirect to login page
```

### Step 3: Requirements Template

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
```

### Step 4: Validation Checklist

- [ ] Each requirement is testable and measurable
- [ ] Requirements cover normal, edge, and error cases
- [ ] User stories provide clear business value
- [ ] Acceptance criteria are specific and unambiguous
- [ ] Requirements are independent and don't conflict
- [ ] All user roles and interactions are addressed

---

## Phase 2: Design

Create comprehensive technical design that bridges requirements and implementation.

### Purpose

The design phase serves to:
- Translate requirements into technical architecture and system design
- Conduct research to inform design decisions
- Define system components, interfaces, and data models
- Establish error handling and testing strategies
- Document design rationale and decision-making process

### Process Overview

```
Requirements → Research → Architecture → Component Design → API Design → Validation → Approved Design
```

### Step 1: Requirements Analysis and Research

**Analyze Requirements:**
- Review each requirement and its technical implications
- Identify areas needing research or clarification
- Consider performance, security, and scalability needs

**Research Areas:**
- Technology stack and framework choices
- Third-party integrations and APIs
- Data storage and management approaches
- Security and compliance considerations
- Performance and scalability patterns

### Step 2: System Architecture

**Architecture Components:**
1. **System Overview**: High-level description of how the system works
2. **Component Architecture**: Major components and their relationships
3. **Data Flow**: How information moves through the system
4. **Integration Points**: External systems and APIs
5. **Technology Stack**: Chosen technologies and rationale

### Step 3: Component Design

**For Each Component:**
- **Purpose**: What the component does
- **Interfaces**: How it connects to other components
- **Responsibilities**: Specific functionality it provides
- **Data Structures**: Key data models and formats
- **Error Handling**: How failures are managed

### Step 4: API and Data Design

**API Design:**
- Endpoint definitions (HTTP methods, paths, parameters)
- Request and response formats
- Authentication and authorization
- Error response patterns

**Data Design:**
- Database schema or data structure definitions
- Relationships between entities
- Data validation rules
- Migration considerations

### Step 5: Design Template

```markdown
# Design Document

## Architecture

### System Overview
[High-level description of system approach]

### Component Architecture
[Major components and their relationships]

### Technology Stack
[Chosen technologies and rationale]

## Components

### Component 1: [Name]
- **Purpose**: [What it does]
- **Key Functions**: [Main functionality]
- **Interfaces**: [How it connects to other parts]
- **Data**: [Key data structures]

### Component 2: [Name]
[Continue for each component...]

## API Design

### Endpoint 1: [Name]
- **Method**: GET/POST/PUT/DELETE
- **Path**: /api/path
- **Request**: [Format and parameters]
- **Response**: [Expected response format]
- **Errors**: [Error handling]

## Data Models

### Model 1: [Name]
```json
{
  "field1": "string",
  "field2": "number",
  "field3": "object"
}
```

## Testing Strategy
[How the design will be tested]

## Error Handling
[How errors are managed throughout the system]
```

### Step 6: Design Validation

- [ ] Design addresses all requirements
- [ ] Components are well-defined with clear responsibilities
- [ ] APIs are complete and consistent
- [ ] Data models support all required operations
- [ ] Error handling is comprehensive
- [ ] Testing approach is defined

---

## Phase 3: Tasks

Break down the approved design into actionable, sequential implementation steps.

### Purpose

The tasks phase serves to:
- Convert design components into specific coding activities
- Sequence tasks for optimal development flow
- Create clear, actionable prompts for implementation
- Establish dependencies and build order
- Enable incremental progress with testable milestones

### Process Overview

```
Design → Task Identification → Task Structuring → Dependency Planning → Task Specification → Ready for Implementation
```

### Step 1: Design Analysis

**Break Down Design:**
- Identify all system components that need to be built
- Map to specific code artifacts (files, classes, functions)
- Consider testing requirements alongside implementation
- Plan for early validation of core functionality

### Step 2: Task Organization

**Principles:**
- **Two-Level Maximum**: Use only top-level tasks and sub-tasks
- **Logical Grouping**: Group related tasks under meaningful categories
- **Sequential Dependencies**: Order tasks so each builds on previous work
- **Testable Increments**: Each task should result in testable functionality

### Step 3: Task Structure

```markdown
- [ ] 1. [Major Component/Epic]
- [ ] 1.1 [Specific implementation task]
  - [Implementation details]
  - [Files/components to create]
  - _Requirements: [Requirement references]_
- [ ] 1.2 [Next specific task]
  - [Task details]

- [ ] 2. [Next Major Component]
- [ ] 2.1 [Specific implementation task]
  - [Task details]
```

### Step 4: Task Specification Template

```markdown
# Tasks Document

## Implementation Plan

### 1. Foundation Setup
- [ ] 1.1 Project structure and dependencies
  - Initialize project with required dependencies
  - Set up development environment configuration
  - _Requirements: All_

- [ ] 1.2 Core data models
  - Define primary data structures
  - Implement validation logic
  - _Requirements: R1, R2_

### 2. Core Functionality
- [ ] 2.1 Authentication system
  - Implement login/logout endpoints
  - Add session management
  - _Requirements: R3, R4_

- [ ] 2.2 Main feature logic
  - Build core business logic
  - Implement API endpoints
  - _Requirements: R5, R6_

### 3. Integration and Testing
- [ ] 3.1 External integrations
  - Connect to third-party APIs
  - Handle integration errors
  - _Requirements: R7_

- [ ] 3.2 Testing and validation
  - Write unit tests for core components
  - Add integration tests
  - _Requirements: All_

## Task Dependencies
[Description of task ordering and dependencies]

## Validation Strategy
[How to verify each task is complete]
```

### Step 5: Task Validation

- [ ] Tasks are specific and actionable
- [ ] Each task produces testable code
- [ ] Dependencies are clear and logical
- [ ] Requirements are traceable to tasks
- [ ] Implementation can proceed incrementally

---

## Implementation and Execution

Execute the planned tasks systematically while maintaining quality.

### Execution Principles

1. **One Task at a Time**: Focus on individual tasks to maintain quality
2. **Validate Early**: Test components as you build them
3. **Document Changes**: Track deviations from the original plan
4. **Maintain Momentum**: Keep implementation moving while ensuring quality

### Task Execution Strategy

**For Each Task:**
1. **Review Context**: Understand the task objective and requirements
2. **Plan Implementation**: Consider approach before coding
3. **Implement Incrementally**: Build in small, testable pieces
4. **Validate Immediately**: Test functionality as soon as possible
5. **Update Documentation**: Note any changes or discoveries

### Quality Gates

**During Implementation:**
- [ ] Code follows established patterns and standards
- [ ] Functionality matches requirements
- [ ] Tests are written and passing
- [ ] Error cases are handled appropriately
- [ ] Documentation is updated

**Before Task Completion:**
- [ ] Acceptance criteria are met
- [ ] Code is reviewed (self or peer)
- [ ] Integration with existing code works
- [ ] No regressions introduced

### Adapting to Discoveries

**When Implementation Reveals Issues:**
1. **Pause and Assess**: Stop coding to understand the issue
2. **Update Specs**: Modify requirements, design, or tasks as needed
3. **Get Approval**: Review changes with stakeholders if necessary
4. **Resume Implementation**: Continue with updated plan

---

## Working with AI

Effective collaboration strategies for AI-assisted spec development and implementation.

### AI Collaboration Principles

1. **Provide Context**: Give AI complete background and relevant information
2. **Be Specific**: Use precise language and clear objectives
3. **Iterate Gradually**: Build complexity through multiple interactions
4. **Validate Output**: Review and refine AI-generated content
5. **Maintain Control**: Use AI as a tool, but maintain decision-making authority

### Prompting Strategies by Phase

#### Requirements Phase

**Effective Prompts:**
```
"Based on this feature idea: [description], help me identify all the user stories and acceptance criteria using EARS format. Consider edge cases and error scenarios."

"Review these requirements and identify any gaps, ambiguities, or missing scenarios: [requirements text]"
```

#### Design Phase

**Effective Prompts:**
```
"Given these requirements: [requirements], help me design a system architecture. Consider scalability, maintainability, and integration requirements."

"I need to design an API for [functionality]. Based on these requirements, what endpoints, request/response formats, and error handling should I include?"
```

#### Tasks Phase

**Effective Prompts:**
```
"Break down this design into specific implementation tasks. Order them for incremental development and early validation: [design]"

"Convert this component design into coding tasks with clear objectives and completion criteria: [component description]"
```

### Best Practices

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

### Common Pitfalls and Solutions

**Problem**: AI generates generic or irrelevant content
**Solution**: Provide more specific context and constraints

**Problem**: AI misunderstands requirements
**Solution**: Break requests into smaller, focused questions

**Problem**: AI suggests overly complex solutions
**Solution**: Ask for simpler alternatives and explain constraints

**Problem**: Inconsistent output across interactions
**Solution**: Provide previous context and maintain conversation history

---

## Conclusion

Spec-driven development provides a systematic approach to transforming ideas into implementable features. By following the three-phase process of Requirements → Design → Tasks, teams can reduce risk, improve quality, and enhance collaboration while leveraging AI tools effectively.

The key to success is applying the methodology strategically—using full specs for complex features, lightweight approaches for simpler work, and skipping specs entirely when appropriate. Remember that the goal is better software delivery, not perfect documentation.

Start with a medium-complexity feature, follow the process, learn from the experience, and adapt the methodology to fit your team's needs and constraints. 