# MCP Server Overview

## What is an MCP Server?

The MCP (Model Control Protocol) server is a backend service designed to extend the capabilities of the Cursor editor and similar code tools. It acts as a bridge between the editor and advanced code intelligence, automation, and integration features.

MCP servers can provide:

- Integration with external APIs and tools
- Custom commands and workflows

Refer to [LLM Ecosystem and Extension](https://ai-skills-baseline.swex.zuluplane.io/Building-GenAI-Solutions/03-LLM-Ecosystem-and-Extension.html) for learnings on MCP Server.

## Role in AI IDE

When integrated with AI IDE like Cursor, the MCP server enables:

- Enhanced code navigation and understanding
- Automated best practice enforcement
- Customizable workflows tailored to team or project needs

## Recommended MCP Servers

| MCP Server | Type | Description |
|------------|------|-------------|
| [Context7 MCP](https://github.com/upstash/context7-mcp) | Context Management | Provides intelligent context management and retrieval for enhanced AI interactions. |
| [DuckDuckGo MCP](https://github.com/nickclyde/duckduckgo-mcp-server) | Search | Instantly search the web for documentation, troubleshooting, and up-to-date info, all without needing an API key. |
| [Figma Dev Mode MCP Server](https://help.figma.com/hc/en-us/articles/32132100833559-Guide-to-the-Dev-Mode-MCP-Server) | Design Integration | Official Figma MCP server that brings Figma directly into your workflow, enabling code generation from selected frames, design context extraction, and Code Connect integration. Currently in open beta. |
| [Figma MCP](https://github.com/GLips/Figma-Context-MCP) | Design Integration | Provides Cursor and other AI coding agents with direct access to Figma layout and design context, enabling accurate code generation from Figma files and nodes. |
| [GitHub MCP](https://github.com/modelcontextprotocol/servers/tree/main/src/github) | Version Control | Integrates GitHub operations into your workflow, letting you manage repositories, issues, pull requests, and content without leaving your environment. |
| [GitLab MCP](https://github.com/smithery-ai/gitlab) | Version Control | Provides GitLab integration for repository management and CI/CD operations. |
| [GitLab MR MCP](https://github.com/kopfrechner/gitlab-mr-mcp) | Code Review | Specialized GitLab merge request management and code review automation. |
| [Knowledge Graph Memory MCP](https://github.com/modelcontextprotocol/servers/tree/main/src/memory) | Memory Management | Maintains persistent project context across sessions, ensuring the AI remembers key details and avoids repetition. |
| [MCP Compass](https://github.com/liuyoshio/mcp-compass) | Discovery | Your navigator for the MCP ecosystem, helping you discover and select the right tools for any task using natural language queries. |
| [Memory Bank MCP](https://github.com/alioshr/memory-bank-mcp) | Memory Management | Automates the creation and management of a hierarchical project memory bank, helping AI understand your project's structure and goals for complex work. |
| [Playwright MCP](https://github.com/microsoft/playwright-mcp) | Web Automation | Provides advanced web automation and cross-browser testing, serving as a modern, feature-rich alternative to Puppeteer. |
| [Puppeteer MCP](https://github.com/modelcontextprotocol/servers/tree/main/src/puppeteer) | Web Automation | Enables website navigation, screenshot capture, and web page interaction, making it invaluable for UI testing and automation tasks. |
| [Sequential Thinking MCP](https://github.com/smithery-ai/server-sequential-thinking) | Problem Solving | Breaks down complex problems into manageable steps, supporting structured problem-solving for system design, architecture, and refactoring. |

## Additional Resources

For a comprehensive list of MCP server directories, communities, and resources, see [MCP Server Resources](mcp-server-resources.md).
