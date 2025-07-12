# 2. Project Setup

Setting up a development project effectively using AI tools and techniques ensures smooth collaboration, high productivity, and adherence to best practices. Below is a detailed guide for initializing your project:

This guide outlines how to set up a development project using AI tools and techniques. A proper setup ensures:
- smooth collaboration
- high productivity
- adherence to best practices

## Initial Setup

1. **Choose Project Platform**
	- select hosting platform (Azure DevOps, GitHub, GitLab, Bitbucket)
	- agree on Git branching strategy
    - document collaboration guidelines

1. **Configure Repository**
    - create GitHub repository manually
    - set branch protection rules

## Development Environment

1. **Configure AI-Powered IDE**
    - **Cursor**
        - Install Cursor
        - Add required VS Code extensions
        - Set up language-specific plugins
    - **GitHub Coplilot**
        - Install GitHub Copliot plugin to VS Code / JetBrains IDE

2. **Configure Privacy Settings - IMPORTANT**
    - In ChatGPT -> Settings -> Data Controls -> "Improve the model for everyone" ->  toggle off / disable
    - In Cursor -> Settings -> General -> Privacy Mode -> enabled

**IMPORTANT:** Privacy settings must be enabled. This ensures that data is not persisted on providers servers and it is not used for training models. 

3. **Add Required Files**
    - copy language-specific rules from [programing language rules](../cursor-rules/languages/README.md)
    - copy framework-specific rules from [framework rules](../cursor-rules/frameworks/README.md)
    - customise IDE rules for team requirements
    - update system prompt for LLM base understanding

## Using Repository Documentation

Create directory within the repository to store documentation, such as:

- product requirements
- architecture documentation
- development rules and guidelines (reference [IDE rules](../cursor-rules/common/README.md))

Ensure all documentation is:

- version controlled
- accessible to the IDE
- formatted in markdown

## Initialize Memory Bank with Tools

Set up the Memory Bank system to enable effective AI assistance throughout the project lifecycle:

1. **Create Memory Bank Structure**
   - install Memory Bank MCP server
   - initialize core memory bank files using prompt: `Initalise memory bank with tools`

2. **Configure Memory Bank Files**
   - `projectbrief.md` - foundation document defining project scope and goals
   - `productContext.md` - user experience goals and problem definition
   - `activeContext.md` - current work focus and recent changes
   - `systemPatterns.md` - architecture and technical decisions
   - `techContext.md` - technologies and development setup
   - `progress.md` - current status and evolution tracking

3. **Integrate with Development Workflow**
   - ensure memory bank files are version controlled
   - establish update patterns for maintaining current context
   - configure AI tools to reference memory bank for project understanding

The Memory Bank serves as the AI assistant's primary reference for understanding project context, enabling more effective and contextually-aware assistance throughout development.

## Next Steps

Once your project setup is complete, proceed to the feature development lifecycle:

**[Functional Requirement](03-functional-requirement.md)** - Start by defining what your system should do from a user's perspective, including expected behaviors, UI elements, and testable features.