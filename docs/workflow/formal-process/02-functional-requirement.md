# 1.1 Functional Requirements

This section provides a structured approach to creating and refining functional requirements for an AI-powered development workflow. Functional requirements define what the system should do from a user's perspective, focusing on expected behaviors, user interface elements, and testable features.

You may spend more than 30% of workflow time on requirement generation and refinement. The more time you invest in this step, the more you can improve the efficiency and quality of the AI-powered development process and save time addressing issues later.

## 1. Understanding Prioritized Feature Requirements

Before embarking on detailed requirement creation, it is essential to clearly understand and prioritize the feature requirements for the service you are developing.

- Collaborate with stakeholders to identify and agree on the key features that align with the overall goals of the project.
- Document these features in order of priority, ensuring alignment with business objectives and technical feasibility.
- Ensure each feature is well-defined and scoped to avoid ambiguities.

## 2. Collaborate with AI to Generate the Feature Description

A detailed feature description should be a *very* detailed account of the feature you want to implement, with as much detail as possible. It's better to err on the side of being very verbose and clear about what you want; the later processes will refine the detail into actionable requirements.

Use a conversational LLM to hone in on the requirement:
[Prompt to act as a Business Analyst](../../prompt-library/product/prompt-business-analyst.md)

Iterate with AI as much as you'd like until you're happy with the outcome.

## 3. Create User Stories and Acceptance Criteria

Save the output from previous step to create comprehensive user stories with testable acceptance criteria.

You can also save the document in the repository in `docs/functional-requirement` folder. It's important that this file is INSIDE the code repository, as we will have the AI-powered IDE reference it later in the workflow.

## 4. Ensuring Functional Requirements Precision

Dedicate substantial time and team effort to refining the functional requirements to eliminate vagueness and potential misinterpretations.

- Ensure all user-facing aspects are reviewed collaboratively by the team.
- Revise any unclear sections to ensure the requirement is unambiguous.
- Validate that all user stories have clear, testable acceptance criteria.
- Ensure accessibility and inclusive design considerations are properly addressed.

## Next Steps

Once your functional requirements are complete, proceed to create the [Technical Specification](02-technical-specification.md) that will define how these functional requirements will be implemented technically.

## Related Resources

- [Prompting Guidance](../../prompt-library/prompting-guidance.md) - Best practices for crafting effective prompts
- [Business Analyst Prompt](../../prompt-library/product/prompt-business-analyst.md) - Specific prompt for requirement generation
- [Project Setup](../project-setup.md) - Ensure your development environment is properly configured
- [Glossary](../../glossary.md) - Key terms and definitions used in this workflow 