# Prompt Library Overview

This library provides a curated selection of prompts designed to optimize your use of AI tools throughout the software development lifecycle. These battle-tested examples serve as guidelines that you can adapt to your specific project needs rather than using them verbatim.

The prompts are organized by workflow stage and purpose, covering everything from initial product specification through development, testing, and documentation. Each prompt includes specific context, clear deliverables, and quality standards to ensure consistent, high-quality outputs.

## Best Practices

- **Start with [Prompting Guidance](prompting-guidance.md)** for detailed guidance on writing effective prompts and maximizing AI tool effectiveness
- **Adapt, don't copy** - Tailor prompts to your project's specific requirements, technology stack, and team conventions
- **Iterate and refine** - Use the prompts as starting points and refine them based on your results and project evolution
- **Combine workflows** - Many prompts work best when used in sequence (e.g., product analysis → data model → API requirements)
- **Reference project context** - Most prompts benefit from including relevant project files, coding standards, or architectural decisions

## Available Prompts

### General
- [Assignment Submission Review](general/prompt-assignement-review.md) - Evaluate assignment submissions and generate a structured HTML report
- [Enhanced Teaching Guidelines](general/prompt-enhanced-teaching-guideline.md) - Guidelines for making AI responses more educational with explanations, alternatives, and interactive learning
- [Human-like Writing](general/prompt-human-like.md) - Make AI responses more natural and human-like by avoiding AI-giveaway phrases and marketing language
- [One-liner Problem Solving](general/prompt-one-liner-probelm-solving.md) - Compact one-liner for quick kick-offs; BLUF, assumptions, clarifications, options/trade-offs, deliverables, and next steps
- [Problem Solving Prompts](general/prompt-problem-solving.md) - A collection of 10 proven problem-solving prompt templates for deep reasoning, critique, and expert emulation
- [Single-shot Coding Prompt](general/prompt-single-shot-coding.md) - Consolidated zero-shot coding template inspired by GPT-5 examples; defines goals, deliverables, UX tokens, data/state, validation, a11y, performance, and acceptance tests
- [Single-shot Problem-Solving](general/prompt-single-shot-problem-solving.md) - Single-round process scaffold for problem framing, assumptions, multi-option trade-offs, expert deep dive, quality gates, and deliverables
- [Technical Assessment Report Generation](general/prompt-technical-assessment.md) - Generate a comprehensive HTML technical review report for the repository with severity-based findings

### Product Specification

These prompts help you define, analyze, and specify product requirements. For optimal results, use them in sequence: start with business analysis, create data models, define APIs, and then specify UI requirements. Refer to [Functional Requirements](../workflow/feature-based-development/02-functional-requirement.md) for detailed workflow guidance.

- [Example Product Requirements Input](product/example-product-requirements-input.md) - Sample product requirements for a governance checklist app showing proper feature specification format
- [API Requirements](product/prompt-api-requirements.md) - Generate RESTful API endpoint specifications from data models with request/response examples
- [Business Analyst Prompt](product/prompt-business-analyst.md) - Generate structured business requirements with goals, stakeholders, assumptions, and BDD acceptance criteria
- [Data Model Generation](product/prompt-data-model-generation.md) - Create database models from business requirements with Mermaid diagrams for MongoDB or relational databases
- [Mobile Design Mockup](product/prompt-mobile-desgin-mockup.md) - Step-by-step workflow to produce mobile UI design screens and a consolidated UI index with TailwindCSS
- [Product Analysis](product/prompt-product-analysis.md) - Conduct meta-analysis of product requirements with pros/cons, recommendations, and alternatives
- [User Interface Requirements](product/prompt-user-interface-requirements.md) - Generate frontend requirements from mockups, data models, and API specifications
- [User Story Creation](product/prompt-user-story-creation.md) - Create detailed user stories with acceptance criteria, UI design, and technical specifications

### Development

These prompts support the implementation phase with code review, testing, and feature development. They emphasize best practices, maintainability, and comprehensive test coverage while following project-specific conventions.

- [Review Merge Request](development/prompt-merge-request-review.md) - Perform a GitLab MR review with inline comments using MCP tools and project-specific rules
- [Create API Integration Test](development/prompt-new-api-integration-test.md) - Create integration tests for API endpoints and flows using Given-When-Then patterns
- [Create End-to-End Test](development/prompt-new-e2e-test.md) - Author Playwright E2E tests with BDD scenarios, optional accessibility scans, and real application interactions
- [Implement New Feature / Story](development/prompt-new-feature-story.md) - Start a new feature with structured design and implementation plan including codebase analysis
- [Create Frontend Integration Test](development/prompt-new-frontend-integration-test.md) - Build integration tests for UI workflows using Jest testing patterns
- [Create Integration Test from Feature](development/prompt-new-integration-test-from-feature.md) - Generate comprehensive integration tests derived from existing features with dependency analysis
- [Refactor Feature](development/prompt-refactor-feature.md) - Guided, incremental refactor focused on readability and consistency with impact assessment

### Documentation

These prompts help create comprehensive technical documentation that explains both the "how" and "why" of your system. They focus on clarity, completeness, and maintainability for various architectural layers.

- [Add / Update Documentation](documentation/prompt-add-update-documentation.md) - Review codebase and create or update README and ARCHITECTURE documentation with British English standards
- [Create API Documentation](documentation/prompt-create-api-documentation.md) - Generate comprehensive API documentation with verification steps, schemas, and implementation details
- [Create Business Logic Documentation](documentation/prompt-create-business-logic-documentation.md) - Document business processes, rules, workflows, and their rationale with integration details
- [Create Repository Documentation](documentation/prompt-create-repository-documentation.md) - Document repository layer architecture, design patterns, and implementation decisions
- [Create Service Layer Documentation](documentation/prompt-create-service-layer-documentation.md) - Document service layer interfaces, business logic, workflows, and architectural decisions
- [Create Technical Design Documentation](documentation/prompt-technical-design-documentation.md) - Develop comprehensive technical design documents with research, architecture, and component details
