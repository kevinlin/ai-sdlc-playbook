# Functional Requirements

This section provides a structured approach to creating and refining functional requirements for an AI-powered development workflow. Functional requirements define what the system should do from a user's perspective, focusing on expected behaviors, user interface elements, and testable features.

You may spend more than 30% of workflow time on requirement generation and refinement. The more time you invest in this step, the more you can improve the efficiency and quality of the AI-powered development process and save time addressing issues later.

## 1. Understanding Prioritised Feature Requirements

Before embarking on detailed requirement creation, it is essential to clearly understand and prioritise the feature requirements for the service you are developing.

- Collaborate with stakeholders to identify and agree on the key features that align with the overall goals of the project.
- Document these features in order of priority, ensuring alignment with business objectives and technical feasibility.
- Ensure each feature is well-defined and scoped to avoid ambiguities.

## 2. Writing a Detailed Feature Description

A detailed feature description should be a *very* detailed account of the feature you want to implement, with as much detail as possible. It's better to err on the side of being very verbose and clear about what you want; the later processes will refine the detail into actionable requirements.

Ideally, this description should take the form of a markdown document, and could look something like this:

```
I'm writing a governance checklist app for governance project tracking. Here are the features of the app:

- This tool allows projects to track their governance process through a unified checklist, composed of multiple governance workflows, each with their own checklist items.
- There can be multiple governance workflows of checklist items, such as a main governance flow, then sub-flows depending on what part of the business you're delivering for.
- The checklist items are general, but should be able to support these types - labels are examples: 'approval' (where the checklist item requires somebody to upload a document as evidence of the approval and state the person, date/time of the approval when checking off), 'document' (where the user must upload the latest version of the document before checking off). I guess 'approval' items also have 'document' item aspects to it, so it's likely they are just two additional types of a normal checklist item (without any states), 'event' could be another type.
- A checklist item should have states (example labels): 'incomplete', 'complete', 'not required'. 
  
...and so on...
```

Consider adding the following to your detailed description:

### 2.1. Overview of the Feature

- A concise description of the feature, outlining its purpose and intended impact.
- How the feature integrates into the existing system or service.

### 2.2. Frontend Requirements

- Specify any changes required for the user interface (UI), including:
    - New components or modifications to existing ones.
    - Specific design guidance, such as layout, colours, typography, and accessibility requirements.
    - Expected user interactions and behaviours.
    - User journey flows and navigation patterns.

### 2.3. User Experience Considerations

- Define the expected user experience, including:
    - User personas and their specific needs.
    - Accessibility requirements and inclusive design considerations.
    - Performance expectations from a user perspective.
    - Error handling and user feedback mechanisms.

### 2.4. Additional Functional Considerations

- Include any other relevant details, such as:
    - Business rules and validation requirements.
    - Integration with existing user workflows.
    - Edge cases and user scenarios.

## 3. Create Interface Mock-ups

Develop interface mock-ups of the screens related to your requirements. This can be done in an advanced tool like Figma, or in an online whiteboard tool such as Miro or Mural. Take screenshots of each mock-up page. Ensure all the elements are clear and readable in the image.

**IMPORTANT:** Make sure you thoroughly annotate the mock-ups with the expected behaviour of each element and the annotations are visible in the screenshots. This will help the LLM better understand the interface requirements in the next step.

## 4. Create Interface Requirements

First upload all mockup screenshots from the previous step using the "wait for more uploads" method with the latest thinking model (e.g. OpenAI o1-mini-high). Since there is a limit of 5 uploads at a time in the ChatGPT interface, upload 5 images, with the prompt "wait for more uploads", then repeat this process until all the images are uploaded. Once all are uploaded, run the following prompt to create the frontend interface requirements:

```
I have the following functional requirements and need to create detailed frontend interface requirements based on the mock-ups I've uploaded. Follow GDS standards and give detail about where the pages should sit (route) and any GDS component design elements:

FUNCTIONAL REQUIREMENTS:
[PASTE FUNCTIONAL REQUIREMENTS HERE]

Please create detailed interface requirements that include:
- Page layouts and component specifications
- User interaction patterns
- Navigation flows
- Accessibility considerations
- Responsive design requirements
- Form validation and error handling
- Content structure and information hierarchy
```

Review the frontend requirements with the team. Refine and re-prompt if required. Save the frontend requirements for later reference.

## 5. Create User Stories and Acceptance Criteria

Using your detailed feature descriptions and interface requirements, create comprehensive user stories with testable acceptance criteria. Use the following prompt with an advanced reasoning model:

```
Based on the following functional requirements and interface specifications, create detailed user stories with acceptance criteria:

FUNCTIONAL REQUIREMENTS:
[PASTE FUNCTIONAL REQUIREMENTS HERE]

INTERFACE REQUIREMENTS:
[PASTE INTERFACE REQUIREMENTS HERE]

For each feature, create user stories in the following format:
- Story title
- User story in "As a [user type], I want [goal], so that [benefit]" format
- Design / UX considerations
- Testable acceptance criteria in Given, When, Then BDD format
- Dependencies on other stories
- Related stories for context

Focus on:
- User-facing functionality
- Expected behaviors and interactions
- Validation and error handling
- Accessibility requirements
- Performance expectations from user perspective
```

## 6. Handling Broken Markdown Files

If the generated markdown file is 'broken':

1. Click the 'copy' icon at the bottom of the ChatGPT chat (this ensures cleaner copying than manual selection and copying).
    
2. Run the copied markdown text through Claude or a similar tool with the following prompt:
    
    ```
    Please convert this to a single file md format. Do not change any of the content:
    
    [PASTE BROKEN MARKDOWN HERE]
    ```

## 7. Deep Functional Analysis of the Solution

Using your functional requirements, conduct a deep analysis to evaluate the user experience and feature effectiveness. Run the following prompt for meta analysis, use an advanced reasoning model:

```
Do some meta analysis to analyse the following functional requirements, focusing on user experience, feature effectiveness, and usability. Come up with a pros and cons list, thinking about how users will interact with this system over its lifetime.

ANALYSIS PHASE:

Read, analyse and understand the following functional requirements:

FUNCTIONAL REQUIREMENTS:
[PASTE HERE]

INTERFACE REQUIREMENTS:
[PASTE HERE]

USER STORIES:
[PASTE HERE]

IMPLEMENTATION PHASE:

Do deep analysis of the proposed solution and write a report detailing the following:
# User Experience Overview
# Feature Effectiveness Analysis
# Usability Over Time
# User Journey Analysis
# Pros and Cons from User Perspective
# Accessibility and Inclusion Assessment
# Recommendations for UX Improvement
# Alternative User Experience Approaches
# User Adoption Considerations
# Long-term User Satisfaction Factors

The report should be in a single, downloadable file using markdown formatting.

VERIFICATION AND COMPLETION PHASE:

- Make sure the analysis covers all user-facing aspects
- Highlight any usability concerns or gaps
- Suggest improvements where possible
```

## 8. Ensuring Functional Requirement Precision

Dedicate substantial time and team effort to refining the functional requirements to eliminate vagueness and potential misinterpretations.

- Ensure all user-facing aspects are reviewed collaboratively by the team.
- Revise any unclear sections to ensure the requirements are unambiguous.
- Validate that all user stories have clear, testable acceptance criteria.
- Ensure accessibility and inclusive design considerations are properly addressed.

## 9. Saving Functional Requirements

Once you have the markdown text, save it in the folder that was set up at the start of the project in `functional-requirements.md` format. It's important that this file is INSIDE the code repository, as we will have the AI-powered IDE reference it later in the workflow.

## A Note About Design and UX

The LLMs have been trained on GDS standards and have ingested GDS style layouts. Therefore, they are often good at determining GDS-compliant designs while they implement features. As long as your functional requirements document and .cursor rules files stipulate adherence to the GDS standards for designs, the LLMs should adhere to them when developing features. The LLMs will also note places in your design where GDS standards are not met and suggest compliant alternatives.

## Next Steps

Once your functional requirements are complete, proceed to create the [Technical Specification](workflow-technical-specification.md) that will define how these functional requirements will be implemented technically. 