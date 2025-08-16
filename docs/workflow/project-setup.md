# Project Setup

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

1. **Configure AI IDE**
    - **Cursor**
        - Install Cursor from [cursor.sh](https://cursor.sh)
        - Add required VS Code extensions (Cursor is built on VS Code)
        - Configure workspace settings and preferences
    - **Kiro**
        - Install Kiro AI IDE
        - Add required VS Code extensions (Kiro is also built on VS Code)
        - Configure workspace settings and preferences
    - **GitHub Copilot**
        - Install GitHub Copilot plugin to VS Code / JetBrains IDE
        - Requires GitHub Copilot subscription

2. **Configure Privacy Settings - IMPORTANT**
    - In ChatGPT -> Settings -> Data Controls -> "Improve the model for everyone" -> toggle off / disable
    - In Cursor -> Settings -> General -> Privacy Mode -> enabled
    - In Kiro -> Configure privacy settings according to your organization's policy
    - In GitHub Copilot -> Settings -> Data retention -> Configure according to your organization's policy

**IMPORTANT:** Privacy settings must be enabled. This ensures that data is not persisted on providers servers and it is not used for training models. 

3. **Add Required Configurations**
    
    **For Cursor:**
    - Copy language-specific rules from [programming language rules](../ide-rules/languages/README.md)
    - Copy framework-specific rules from [framework rules](../ide-rules/frameworks/README.md)
    - Customize IDE rules for team requirements
    - Update system prompt for LLM base understanding
    
    **For Kiro:**
    - Set up steering guidelines in `.kiro/steering/` directory
    - Configure project-specific steering rules for consistent AI behavior
    - Add team standards and coding conventions to steering files
    - Refer to `.kiro/steering` documentation for detailed configuration options

## Using Repository Documentation

Create directory within the repository to store documentation, such as:

- product requirements
- architecture documentation
    - development rules and guidelines (reference [IDE rules](../ide-rules/common/README.md))

Ensure all documentation is:

- version controlled
- accessible to the IDE
- formatted in markdown

## (Optinal) Initialize Memory Bank with Tools

Set up the Memory Bank system to enable effective AI assistance throughout the project lifecycle:

1. **Create Memory Bank Structure**
   - install Memory Bank MCP server
   - initialize core memory bank files using prompt: `Initialize memory bank with tools`

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

## (Optional) Configure VibeSpecs MCP Server for Spec-Driven Development

Set up the VibeSpecs MCP Server to enable structured, spec-driven development workflow in Cursor:

1. **Install VibeSpecs MCP Server**
   - follow installation instructions from [VibeSpecs MCP Server](https://github.com/yinwm/vibedevtools/tree/main/vibedev-specs-mcp)
   - configure the server in your Cursor MCP settings

2. **Initialize Spec-Driven Workflow**
   - use the workflow commands to guide feature development from requirements to implementation
   - leverage structured phases: goal definition → requirements → design → tasks → execution

3. **Integrate with Project Structure**
   - align spec outputs with your repository documentation structure
   - ensure generated specifications are version controlled
   - reference [spec-driven development documentation](spec-driven-development/README.md) for best practices

The VibeSpecs MCP Server provides a systematic approach to feature development, ensuring thorough planning and consistent implementation across your project.

## Next Steps

Once your project setup is complete, proceed to the feature development lifecycle:

**[Functional Requirements](feature-based-development/02-functional-requirement.md)** - Start by defining what your system should do from a user's perspective, including expected behaviors, UI elements, and testable features.