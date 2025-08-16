# Prompt Library Overview

This library provides a curated selection of prompts to optimize your use of AI tools in the development workflow. These examples serve as guidelines that you can adapt to your specific project needs rather than using them verbatim.

## Best Practices
- Refer to [Prompting Guidance](prompting-guidance.md) for detailed guidance on writing effective prompts
- Tailor prompts to your project's specific requirements
- Iterate and refine prompts based on results

## Available Prompts

### General
- [Assignment Submission Review](documentation/prompt-assignement-review.md) - Evaluate assignment submissions and generate a structured HTML report
- [Enhanced Teaching Guideline](general/prompt-enhanced-teaching-guideline.md)
- [Human-like Writing](general/prompt-human-like.md) - Make AI responses more natural and human-like
- [One-liner Problem Solving](general/prompt-one-liner-probelm-solving.md) - Compact one-liner for quick kick-offs; BLUF, assumptions, clarifications, options/trade-offs, deliverables, and next steps
- [Problem Solving Prompts](general/prompt-problem-solving.md) - A Collection of Prompts for Problem Solving
- [Single-shot Coding Prompt](general/prompt-single-shot-coding.md) - Consolidated zero-shot coding template inspired by GPT-5 examples; defines goals, deliverables, UX tokens, data/state, validation, a11y, performance, and acceptance tests
- [Single-shot Problem-Solving](general/prompt-single-shot-problem-solving.md) - Single-round process scaffold for problem framing, assumptions, multi-option trade-offs, expert deep dive, quality gates, and deliverables
- [Technical Assessment Report Generation](general/prompt-technical-assessment.md) - Generate a comprehensive HTML technical review report for the repository


### Product Specification
For understanding of product requirements prompt sequencing, please refer to the workflow steps in [Functional Requirements](../workflow/feature-based-development/02-functional-requirement.md)

- [Example Product Requirements Input](product/example-product-requirements-input.md)
- [API Requirements](product/prompt-api-requirements.md)
- [Business Analyst Prompt](product/prompt-business-analyst.md) - Generate structured business requirements with goals, stakeholders, assumptions, and BDD acceptance criteria
- [Data Model Generation](product/prompt-data-model-generation.md)
- [Mobile design mockup](product/prompt-mobile-desgin-mockup.md) - Step-by-step workflow to produce mobile UI design screens and a consolidated UI index
- [Deep Product Analysis](product/prompt-product-analysis.md)
- [User Interface Requirements](product/prompt-user-interface-requirements.md)
- [User Story Creation](product/prompt-user-story-creation.md)

### Development
- [Review Merge Request](development/prompt-merge-request-review.md) - Perform a GitLab MR review with inline comments using MCP tools
- [Create API Integration Test](development/prompt-new-api-integration-test.md) - Create integration tests for API endpoints and flows
- [Create End-to-End Test](development/prompt-new-e2e-test.md) - Author Playwright E2E tests, with optional accessibility scan
- [Implement New Feature / Story](development/prompt-new-feature-story.md) - Start a new feature with a structured design and implementation plan
- [Create Frontend Integration Test](development/prompt-new-frontend-integration-test.md) - Build integration tests for UI workflows
- [Create Integration Test from Feature](development/prompt-new-integration-test-from-feature.md) - Generate integration tests derived from an existing feature
- [Refactor Feature](development/prompt-refactor-feature.md) - Guided, incremental refactor focused on readability and consistency

### Documentation
- [Add / Update Documentation](documentation/prompt-add-update-documentation.md)
- [Create API Documentation](documentation/prompt-create-api-documentation.md)
- [Create Business Logic Documentation](documentation/prompt-create-business-logic-documentation.md)
- [Create Repository Documentation](documentation/prompt-create-repository-documentation.md)
- [Create Service Layer Documentation](documentation/prompt-create-service-layer-documentation.md)
- [Create Technical Design Documentation](documentation/prompt-technical-design-documentation.md)
