---
description: MCP server for spec-driven development workflow automation, enabling structured feature development through AI assistance.
---

# Spec-driven Development MCP Server

## Overview

The Spec-driven Development MCP Server is an AI-guided workflow tool that brings structured, step-by-step development guidance to any AI-powered IDE. It transforms the development process by emphasizing detailed specifications before writing code, ensuring clear requirements, better design decisions, and more maintainable code.

## What is Spec-driven Development?

Spec-driven development is a methodology that emphasizes creating detailed specifications before writing code. This approach helps ensure:

- Clear requirements and expectations
- Better design decisions upfront
- More maintainable and predictable code
- Structured documentation throughout the development process

## Key Features

- **Complete Development Workflow**: Guides you from initial goal collection through to final task execution
- **AI-Powered Guidance**: Provides step-by-step instructions for each development phase
- **Structured Documentation**: Automatically generates organized specifications using the EARS (Easy Approach to Requirements Syntax) format
- **Template-Based Approach**: Uses proven templates for requirements gathering, design documentation, and task planning

## Installation

### Using npx (Recommended)

```bash
# Always get the latest version
npx spec-driven-dev-mcp@latest

# Or simply (will also get latest)
npx spec-driven-dev-mcp
```

### Using npm

```bash
npm install -g spec-driven-dev-mcp
spec-driven-dev-mcp
```

## Configuration

### Cursor Integration

Add the following configuration to your Cursor MCP settings:

```json
{
  "mcpServers": {
    "spec-driven-dev-mcp": {
      "command": "npx",
      "args": ["spec-driven-dev-mcp@latest"],
      "env": {},
      "disabled": false
    }
  }
}
```

## Available Tools

The MCP server provides nine distinct tools that guide you through the complete development workflow:

1. **spec_driven_dev_workflow_start** - Initiates the development workflow
2. **spec_driven_dev_goal_confirmed** - Confirms and locks in feature goals
3. **spec_driven_dev_requirements_start** - Begins the requirements gathering phase
4. **spec_driven_dev_requirements_confirmed** - Confirms requirements completion
5. **spec_driven_dev_design_start** - Starts the design documentation phase
6. **spec_driven_dev_design_confirmed** - Confirms design completion
7. **spec_driven_dev_tasks_start** - Begins task planning and breakdown
8. **spec_driven_dev_tasks_confirmed** - Confirms task planning completion
9. **spec_driven_dev_execute_start** - Starts the implementation phase

## Workflow Stages

The spec-driven development process follows five distinct stages:

### 1. Goal Collection

**Purpose**: Establish clear, specific objectives for your feature.

Define what you want to build with specific details about:

- Feature scope and boundaries
- Required functionality
- Integration requirements
- User roles and permissions

### 2. Requirements Gathering

**Purpose**: Transform goals into specific, testable requirements using EARS format.

Creates detailed requirements documents that include:

- Functional requirements in EARS syntax
- User story specifications
- Acceptance criteria
- Business rules and constraints

### 3. Design Documentation

**Purpose**: Create comprehensive technical specifications.

Generates detailed design documentation covering:

- System architecture and component design
- Database schemas and data models
- API specifications and endpoints
- Authentication and authorization flows
- Integration patterns and middleware

### 4. Task Planning

**Purpose**: Break down the feature into executable development tasks.

Creates a structured task breakdown including:

- Numbered, prioritized task list
- Clear task dependencies
- Implementation order recommendations
- Testing and validation checkpoints

### 5. Task Execution

**Purpose**: Implement the feature according to specifications.

Guides systematic implementation:

- Step-by-step code implementation
- Following established design patterns
- Maintaining consistency with specifications
- Building comprehensive test coverage

## Generated Project Structure

Throughout the workflow, the following documentation structure is automatically created:

```
.docs/specs/{feature_name}/
├── requirements.md    # EARS-format requirements
├── design.md         # Technical architecture and design
└── tasks.md          # Implementation checklist and breakdown
```

## Example Workflow

Here's how the workflow operates with a practical example - building a user authentication feature:

### Goal Collection Example
```
User: I want to build a user authentication feature
Assistant: Let me start the spec-driven development workflow for you.

Questions to clarify your goals:
1. What specific authentication methods do you want to support?
2. Do you need social login (Google, GitHub, etc.)?
3. What user roles and permissions are required?

User: I need email/password login with JWT tokens, plus Google OAuth, and basic user/admin roles.

Confirmed goals:
- Feature: User authentication system
- Methods: Email/password + Google OAuth  
- Tokens: JWT-based
- Roles: User and Admin
- Feature name: "user-authentication"
```

### Requirements Generation Example
```
Assistant: Now let's gather detailed requirements in EARS format.

Generated requirements include:
- WHEN a user provides valid email/password THEN the system SHALL authenticate them
- GIVEN a user wants Google OAuth WHEN they click "Sign in with Google" THEN the system SHALL redirect to Google
- WHERE user roles are needed IF user is admin THEN they SHALL access admin features
```

### Design Documentation Example
```
Assistant: Creating technical design documentation.

Generated design includes:
- Database schema for users, sessions, oauth_tokens
- Authentication middleware architecture
- JWT token structure and validation flow  
- Google OAuth integration endpoints
- Role-based access control implementation
```

### Task Planning Example
```
Assistant: Breaking down into executable tasks.

Generated task list:
1. Set up database models (User, Session, OAuthToken)
2. Implement JWT token service
3. Create email/password authentication endpoints
4. Integrate Google OAuth flow
5. Build role-based middleware
6. Add frontend login/register forms
7. Write integration tests
```

## Benefits

### For Development Teams

- **Consistency**: Ensures all team members follow the same structured approach
- **Documentation**: Automatically generates comprehensive project documentation
- **Quality**: Reduces bugs and technical debt through upfront planning
- **Maintainability**: Creates clear specifications that make future changes easier

### For Project Management

- **Visibility**: Clear tracking of development progress through structured phases
- **Predictability**: Better estimation and planning through detailed task breakdown
- **Risk Mitigation**: Early identification of technical challenges and dependencies

### For Code Quality

- **Architecture**: Promotes thoughtful system design before implementation
- **Testing**: Integrates testing considerations into the planning process
- **Standards**: Enforces consistent coding patterns and practices

## When to Use

Spec-driven development is particularly valuable for:

- **Complex Features**: Multi-component features with multiple integration points
- **Team Projects**: When multiple developers need to coordinate work
- **Mission-Critical Code**: Systems where reliability and maintainability are paramount
- **Learning Projects**: When you want to develop good development practices
- **Legacy Modernization**: When updating or replacing existing systems

## Best Practices

### Getting Started

1. **Start Small**: Begin with a simple feature to learn the workflow
2. **Be Specific**: Provide detailed answers during goal collection
3. **Review Thoroughly**: Carefully review each generated document before proceeding
4. **Iterate**: Don't hesitate to refine requirements or design based on new insights

### During Development

1. **Follow the Order**: Complete each phase before moving to the next
2. **Document Changes**: Update specifications if requirements change during implementation
3. **Test Early**: Use the generated task breakdown to implement testing alongside features
4. **Reference Specs**: Regularly refer back to the generated documentation during coding

## Related Resources

- [MCP Server Overview](README.md) - General information about MCP servers
- [Memory Bank](memory-bank.md) - Complementary context management approach
- [MCP Server Resources](mcp-server-resources.md) - Additional MCP server tools

## Links

- [GitHub Repository](https://github.com/kevinlin/spec-driven-dev-mcp)
- [NPM Package](https://www.npmjs.com/package/spec-driven-dev-mcp)