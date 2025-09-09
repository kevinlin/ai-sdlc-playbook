---
description: This section provides a structured approach to creating and refining functional requirements for an AI-powered development workflow. Functional requirements define what the system should do from a user's perspective.
---

# 2. Functional Requirements

This section provides a structured approach to creating and refining functional requirements for an AI-powered development workflow. Functional requirements define what the system should do from a user's perspective, focusing on expected behaviors, user interface elements, and testable features.

You may spend more than 30% of workflow time on requirement generation and refinement. The more time you invest in this step, the more you can improve the efficiency and quality of the AI-powered development process and save time addressing issues later.

## 1. Start With Your Feature Description

You will get the best outcomes from AI by first clearly articulating the requirement in your own words. 

Create a comprehensive markdown document describing the feature you want to implement. Include these elements where relevant:

- **Purpose and scope** - What are we going to do?
- **User interactions** - How will people use this feature?
- **Frontend requirements** - Interface elements, user flows and visual design needs
- **Backend requirements** - Processing logic, data handling and system behaviour
- **Data considerations** - What information you'll store, process or display
- **Business rules** - Constraints, validations and compliance requirements
- **Integration points** - How this connects with existing systems
- **Performance expectations** - Speed, capacity and reliability requirements
- **Security requirements** - Authentication, authorisation and data protection needs

Write with detail and clarity about what you want - this clarifies your own thinking and expectations of what is to be generated, and it forms the foundation for AI-generated artefacts.

### Example Feature Description

```markdown
I'm creating a governance checklist app for governance project tracking. Here are the features of the app:

- This tool allows projects to track their governance process through a unified checklist, composed of multiple governance workflows, each with their own checklist items.
- There can be multiple governance workflows of checklist items, such as a main governance flow, then sub-flows depending on what part of the business you're delivering for.
- The checklist items are general, but should be able to support these types - labels are examples: 'approval' (where the checklist item requires somebody to upload a document as evidence of the approval and state the person, date/time of the approval when checking off), 'document' (where the user must upload the latest version of the document before checking off). I guess 'approval' items also have 'document' item aspects to it, so it's likely they are just two additional types of a normal checklist item (without any states), 'event' could be another type.
- A checklist item should have states (example labels): 'incomplete', 'complete', 'not required'. 
  
...and so on...
```

Use a conversational LLM to hone in on the requirement:
[Prompt to act as a Business Analyst](../../prompt-library/product/prompt-business-analyst.md)

Iterate with AI as much as you'd like until you're happy with the outcome.

## 2. Create Visual Mockups

For user-facing features, develop mockups using Figma, Miro or similar tools. Add clear annotations explaining expected behaviours, user flows and interaction patterns.

**Why this matters**: Visual references help AI tools understand your interface requirements and generate more accurate implementations. Include:

- Key user journeys and decision points
- Error states and edge cases
- Responsive behaviour for different screen sizes
- Accessibility considerations

You can use [prompt-user-interface-requirements](../../prompt-library/product/prompt-user-interface-requirements.md) in an AI Assistant to create a text description of the interface that can then be used with the language model when you do code generation. 

## 3. Generate PRD

When your situation requires formal documentation, for example a new epic, use AI Assistants to generate Product Requirements Documents (PRDs) containing requirements, features and user stories together using [prompt-combined-requirements-features-stories](../../prompt-library/product/prompt-combined-requirements-features-stories.md). Refine through iterative conversation.

## 4. Generate User Stories

When your situation requires user stories, use [prompt-user-story-creation](../../prompt-library/product/prompt-user-story-creation.md) in an AI Assistant to create a detailed story with acceptance criteria. Refine through iterative conversation.

## Next Steps

Once your functional requirements are complete, proceed to create the [Technical Specification](03-technical-specification.md) that will define how these functional requirements will be implemented technically.

## Related Resources

- [Prompting Guidance](../../prompt-library/prompting-guidance.md) - Best practices for crafting effective prompts
- [Project Setup](../project-setup.md) - Ensure your development environment is properly configured
- [Glossary](../../glossary.md) - Key terms and definitions used in this workflow 