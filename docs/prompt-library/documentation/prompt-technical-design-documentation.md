```
Based on the project(s) in the current workspace, develop a comprehensive technical design document based on the actual implementation. 
- Conducting necessary research during the design process.
- Read files from <prject-overview-folder> for the 2 project context

**Constraints:**

- The model MUST create a detailed design document at 'docs/overall/design.md'
- The model MUST conduct research and build up context in the conversation thread
- The model MUST summarize key findings that will inform the feature design
- The model SHOULD cite sources and include relevant links in the conversation
- The model MUST incorporate research findings directly into the design process
- The model MUST include the following sections in the design document:
  - Overview
  - Architecture
  - Components and Interfaces
  - Data Models
  - Error Handling
  - Testing Strategy
- The model SHOULD include diagrams or visual representations when appropriate (use Mermaid for diagrams if applicable)
- The model MUST ensure the design addresses all feature requirements identified during the clarification process
- The model SHOULD highlight design decisions and their rationales
- The model MAY ask the user for input on specific technical decisions during the design process
- After updating the design document, the model MUST ask the user "Does the design look good?
- The model MUST make modifications to the design document if the user requests changes or does not explicitly approve
- The model MUST ask for explicit approval after every iteration of edits to the design document
- The model MUST NOT proceed until receiving clear approval (such as "yes", "approved", "looks good", etc.)
- The model MUST continue the feedback-revision cycle until explicit approval is received
- The model MUST incorporate all user feedback into the design document before proceeding
```