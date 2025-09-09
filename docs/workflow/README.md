---
description: This section outlines workflows for integrating AI into the development lifecycle. Start with project setup, then choose the workflow that best fits your project needs and team structure.
---

# AI Development Workflow

This section outlines workflows for integrating AI into the development lifecycle. Start with project setup, then choose the workflow that best fits your project needs and team structure.

## Getting Started

**[Project Setup](project-setup.md)** - Define foundational elements, tools, and conventions (start here for all workflows)

---

## Choose Your Development Workflow

We provide three complementary approaches for different project needs:

### 1. Feature-Based Development
**Best for:** Enterprise projects, complex systems, and team-based development requiring thorough documentation and process adherence.

**Get Started:**

- **[Functional Requirements](feature-based-development/02-functional-requirement.md)** - Define expected behavior and user experience

**Complete Process:**

1. [Functional Requirements](feature-based-development/02-functional-requirement.md) - Define expected behavior, UI, testable features, and user experience using AI tools to draft and refine
2. [Technical Design](feature-based-development/03-technical-design.md) - Define technical implementation, data models, API endpoints, and backend architecture
3. [Development](feature-based-development/04-development.md) - Develop the solution iteratively, leveraging AI for implementation
4. [Testing](feature-based-development/05-testing.md) - Unit, functional and end-to-end testing
5. [Refactoring](feature-based-development/06-refactoring.md) - Refactor once feature complete
6. [Documentation](feature-based-development/07-documentation.md) - Update all relevant documentation to reflect changes

**Use when:**

- Building complex features with multiple components
- Working across multiple teams or stakeholders
- Documentation and knowledge preservation are critical
- Following formal development processes

### 2. Spec-Driven Development
**Best for:** Systematic requirements management with AI-optimized planning before implementation.

**Get Started:**

- **[Overview](spec-driven-development/README.md)** - Quick introduction and decision framework
- **[Process Guide](spec-driven-development/process/README.md)** - Three-phase methodology from idea to implementation
- **[Examples](spec-driven-development/examples/README.md)** - Real specs and case studies

**Three-Phase Process:**

1. **Requirements** - Transform vague ideas into clear, testable requirements
2. **Design** - Create comprehensive technical plans for implementation
3. **Tasks** - Break down designs into actionable, sequential implementation steps

**Use when:**

- Features involve multiple components or integrations
- Working on high-stakes projects where failure is costly
- Coordinating work across multiple developers or teams
- Using AI tools that benefit from structured context
- Requirements are complex or likely to change

### 3. Vibe Coding Plus
**Best for:** Rapid prototyping, small projects, and situations where speed and flexibility are prioritized.

**Get Started:**

- **[Vibe Coding Plus Workflow](vibe-coding-plus.md)** - Streamlined approach for rapid development

**Use when:**

- Building experimental prototypes
- Working on small, well-understood features
- Time-critical development
- Solo development or small teams
- Iterating quickly on ideas

---

## Additional Resources

**[Learning with AI](learning.md)** - Continuous learning and skill development with AI assistance

## Choosing the Right Workflow

| Factor | Feature-Based | Spec-Driven | Vibe Coding Plus |
|--------|---------------|-------------|------------------|
| **Project Size** | Large, complex | Medium to large | Small to medium |
| **Team Size** | Multiple agile teams | 1-10 developers | single developers |
| **Documentation** | Comprehensive | Structured | Minimal |
| **Planning Time** | Extensive | Moderate | Minimal |
| **Risk Tolerance** | Low | Low-Medium | Medium-High |
| **Change Frequency** | Low | Medium | High |

**Not sure which to choose?** Start with [Project Setup](project-setup.md), then try Spec-Driven Development for your first AI-assisted feature to learn the principles before adapting to your team's needs.
