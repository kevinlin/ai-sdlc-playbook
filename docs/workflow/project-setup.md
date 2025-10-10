---
description: Setting up a development project effectively using AI tools and techniques ensures smooth collaboration, high productivity, and adherence to best practices.
---

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

### 1. Choose Your AI IDE or Extension

Select an AI-powered development environment that fits your workflow:

- **[Cursor](https://cursor.sh)** - AI-first code editor with built-in AI chat and editing (subscription required)
- **[Kiro](https://kiro.ai)** - AI IDE with steering documents for consistent AI behavior (subscription required)
- **[GitHub Copilot](https://github.com/features/copilot)** - AI pair programmer available as VS Code/JetBrains plugin (subscription required)
- **[Claude Code](https://claude.ai/code)** - AI coding agent by Anthropic, available as CLI and IDE extension (Claude Pro subscription required)
- **[OpenAI Codex](https://openai.com/codex/)** - AI coding agent by OpenAI, available as cloud service, CLI tool, and IDE extensions (subscription required)

### 2. Install IDE and Required Plugins

**For Cursor and Kiro:**

- Download and install the IDE (both are built on VS Code)
- Install required VS Code extensions for your tech stack
- Configure workspace settings and preferences

**For GitHub Copilot:**

- Install GitHub Copilot extension in VS Code or JetBrains IDE
- Sign in with GitHub account

**For Claude Code:**

- Install Claude Code CLI from [claude.ai/code](https://claude.ai/code)
- Subscribe to Claude Pro for access
- Optional: Install [VS Code extension](https://docs.claude.com/en/docs/claude-code/vs-code) for IDE integration
- See [Claude Code Settings](https://docs.claude.com/en/docs/claude-code/settings) for configuration options

**For OpenAI Codex:**

- Install IDE extension from marketplace or use CLI tool
- Configure API access with OpenAI API key
- See [Codex IDE Configuration](https://developers.openai.com/codex/ide) for setup details

### 3. Configure Privacy Settings

**IMPORTANT:** Privacy settings must be enabled. This ensures that data is not persisted on providers' servers and is not used for training models.

- **ChatGPT**: Settings -> Data Controls -> "Improve the model for everyone" -> toggle off/disable
- **Cursor**: Settings -> General -> Privacy Mode -> enabled
- **Kiro**: Configure privacy settings according to your organization's policy
- **GitHub Copilot**: Settings -> Data retention -> Configure according to your organization's policy
- **Claude Code**: Configure via [settings files](https://docs.claude.com/en/docs/claude-code/settings)
- **OpenAI Codex**: TBA

### 4. Configure IDE Rules

IDE rules guide AI behavior and provide context about your project. Learn more in [IDE Rules Overview](../ide-rules/README.md).

**Common Steps for All IDEs:**

- Copy language-specific rules from [programming language rules](../ide-rules/languages/README.md)
- Copy framework-specific rules from [framework rules](../ide-rules/frameworks/README.md)
- Customize rules for your team's requirements and coding standards
- Update system prompt for LLM base understanding

**IDE-Specific Rule Configuration:**

**For Cursor:**

- Enable Rules & Memories in Cursor Settings:
    - Go to Settings -> Features -> Rules & Memories
    - Enable "Include CLAUDE.md in context" - adds CLAUDE.md and CLAUDE.local.md files to the agent's context when relevant
    - Enable "Import Claude Commands" - loads commands from .claude/commands directories alongside .cursor/commands
- Store rules in `.cursor/rules/` directory using MDC format
    - Support for Always, Auto Attached, Agent Requested, and Manual rule types

**For Kiro:**

- Store steering documents in `.kiro/steering/` directory
    - Configure file match patterns for conditional inclusion
    - Support for Always Included, File Match Conditional, and Manual Inclusion

**For Claude Code:**

- User-level:
    - Create `~/CLAUDE.md` file for custom user prompts
    - Create `~/.claude/settings.json` for global configurations
    - Store personal commands in `~/.claude/commands/` directory (user-level)
- Project-level:
    - Create `CLAUDE.md` file in repository root for project context and instructions
    - Create `.claude/settings.json` for project-level configuration (shared with team)
    - Create `.claude/settings.local.json` for personal settings (not checked into source control)
    - Store commands in `.claude/commands/` directory (project-level)
- Configure permissions, environment variables, and hooks in settings files
- See [Claude Code Settings documentation](https://docs.claude.com/en/docs/claude-code/settings) for complete configuration options

**For OpenAI Codex:**

- Configure IDE-specific settings according to [Codex IDE configuration](https://developers.openai.com/codex/ide)
- Set up API key and model preferences
- Create project-specific configuration files as needed

### 5. Set Up Slash Commands

Slash commands reduce token consumption and enable reusable workflows. Learn more in [Slash Commands Guide](../slash-command/README.md).

**For Cursor:**

- Commands stored in `.cursor/commands/` directory
- Also supports `.claude/commands/` when "Import Claude Commands" is enabled

**For Claude Code:**

- Project commands in `.claude/commands/` - appear as `(project)` in `/help`
- Personal commands in `~/.claude/commands/` - appear as `(user)` in `/help`
- Create Markdown files - filename becomes the command name
- Support for namespacing with subdirectories


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
    - Install [Memory Bank MCP](https://github.com/ipospelov/mcp-memory-bank)
    - Initialize core memory bank files using prompt: `Initialize memory bank with tools`
2. **Configure Memory Bank Files**
    - `projectbrief.md` - foundation document defining project scope and goals
    - `productContext.md` - user experience goals and problem definition
    - `activeContext.md` - current work focus and recent changes
    - `systemPatterns.md` - architecture and technical decisions
    - `techContext.md` - technologies and development setup
    - `progress.md` - current status and evolution tracking
3. **Integrate with Development Workflow**
    - Ensure memory bank files are version controlled
    - Establish update patterns for maintaining current context
    - Configure AI tools to reference memory bank for project understanding

The Memory Bank serves as the AI assistant's primary reference for understanding project context, enabling more effective and contextually-aware assistance throughout development.

## (Optional) Configure MCP Server for Spec-Driven Development

Set up the VibeSpecs MCP Server to enable structured, spec-driven development workflow in Cursor / VS Code:

1. **Install VibeSpecs MCP Server**
    - Follow installation instructions from [Spec-Diven Dev MCP](https://github.com/kevinlin/spec-coding-mcp)
    - Configure the server in your Cursor MCP settings
2. **Initialize Spec-Driven Workflow**
    - Use the workflow commands to guide feature development from requirements to implementation
    - Leverage structured phases: goal definition → requirements → design → tasks → execution
3. **Integrate with Project Structure**
    - Align spec outputs with your repository documentation structure
    - Ensure generated specifications are version controlled
    - Reference [Spec-Driven Development](spec-driven-development/README.md) for best practices

The Spec-Driven Dev MCP Server provides a systematic approach to feature development, ensuring thorough planning and consistent implementation across your project.

## Next Steps

Once your project setup is complete, proceed to the feature development lifecycle:

**[Requirement Specification](feature-based-development/02-requirement-specification.md)** - Start by defining what your system should do from a user's perspective, including expected behaviors, UI elements, and testable features.
