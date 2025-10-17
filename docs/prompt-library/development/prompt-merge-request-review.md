# GitLab Merge Request Review Prompt
Perform code review on a GitLab merge request, add in-line comments and a summary.

## Prerequisites

**Required MCP Servers:** This prompt requires the following MCP servers to be active and properly configured:

1. **gitlab-mr-mcp** - For interacting with GitLab merge requests
    - **Installation:** Follow the setup instructions in [GitLab MR MCP](https://github.com/kevinlin/gitlab-mr-mcp)

2. **context7** - For fetching version-specific library documentation
    - **Installation:** Follow the setup instructions in [Context7 MCP CMP](https://github.com/upstash/context7)

Before running this prompt:

- Check that both MCP servers show active status
- If a server appears inactive, try toggling it **Off/On** and refresh
- Wait for the status to show active before proceeding

```
---
argument-hint: [mr-number]
description: Structured prompt for conducting thorough merge request reviews with quality and security checks.
---

Please help me review merge request #[$1] of the current project.

## Step 1: Fetch Merge Request Information

Make use of MCP tools from `gitlab-mr-mcp` MCP server:

- DO NOT call `get-projects`, instead getting project id from `general.mdc` 
- Call `get_merge_request_details`, `get_merge_request_diff`, `get_merge_request_comments` to fetch merge request details
- Call `add_merge_request_comment` and `add_merge_request_diff_comment` to add comments to the merge request

## Step 2: Load Project Context

First, analyze the file types that have been changed in this merge request and load the appropriate IDE rules based on file types:
- Cursor IDE: `.cursor/rules/`
- Kiro: `.kiro/steering/`

Apply the appropriate rules when reviewing each file and ensure your feedback aligns with the project's established conventions as defined in these ruleset files.

## Step 3: Load Library Documentation

For code changes that involve external libraries or frameworks:

1. Identify the libraries and frameworks used in the changed code by examining:
    - Import/require statements in the modified files
    - Package dependency files (e.g., `package.json`, `requirements.txt`, `pom.xml`, `go.mod`, `Gemfile`, etc.)
2. For each identified library:
    - Use `resolve-library-id` to get the Context7-compatible library ID
    - Use `get-library-docs` with the resolved library ID to fetch version-specific documentation
    - Focus the documentation topic on the specific functionality being used or modified
3. Use the fetched documentation to:
    - Verify that library APIs are being used correctly according to the declared version
    - Check for deprecated methods or patterns
    - Identify better practices or more appropriate APIs
    - Ensure compatibility with the declared dependency versions

## Coding Guidelines
Please follow these guidelines for the review:

1. Code Quality & Standards:
    - Follow language-specific best practices according to the IDE rules
    - Ensure proper error handling and type safety where applicable
    - Check for code duplication and unnecessary complexity
    - Verify naming conventions and code formatting based on project standards
    - Look for potential memory leaks or performance issues
    - Ensure architecture principles are followed (e.g., hexagonal architecture for TypeScript)
    - Verify library usage against fetched documentation
    - Check that APIs, methods, and patterns align with the version-specific documentation from Context7
2. Configuration & Environment:
    - Review environment variable changes
    - Check configuration file modifications
    - Verify deployment and infrastructure changes
    - Ensure secrets and sensitive data are handled properly
3. Documentation:
    - Verify README.md and documentation updates follow the standards in markdown.mdc
    - Check for clear and accurate documentation updates
    - Ensure configuration changes are properly documented
    - Look for missing documentation on new features
4. Testing & Reliability:
    - Look for missing test coverage
    - Check error handling scenarios
    - Verify edge cases are considered
    - Suggest additional test scenarios if needed
5. Performance & Scalability:
    - Review database queries and indexes
    - Check caching strategies and implementation
    - Look for N+1 query problems
    - Verify connection pooling and resource management
6. Security:
    - Check for security vulnerabilities
    - Verify proper input validation
    - Ensure secure handling of user data
    - Review authentication and authorization changes

## Outcome
Add review comments directly to GitLab merge request:

1. General comment that start with overall summary, followed by all the findings.
2. Detailed inline comments on specific code sections that expect code changes
3. DO NOT include a Final Summary comment

### General Comment Guidelines

The general comment should include:

- Overall assessment of the merge request
- Summary of all findings (both positive and areas for improvement)
- High-level observations about code quality, architecture, and adherence to project standards

### Inline Comment Guidelines

**Content Requirements:**

- Address **one issue or suggestion only** - keep each comment atomic and focused
- Be concise and action-focused - get straight to the point
- Keep messages short - avoid lengthy explanations
- **Do NOT add inline comments for positive feedback** - save praise for the general comment
- Only comment on issues that require changes or attention
- Skip comments only about documentation changes

**Structure and Format:**

- Make it clear the comment is made by [you] (Claude Code, Cursor, Codex, etc)
- Include file names and line numbers
- The inline comment should be inserted right after the code referring to (line number + 1)
- Reference the specific IDE rule that applies, if applicable
- Reference the library documentation when suggesting changes to library usage (cite the specific API version and method from Context7)

**Quality Standards:**

- Be specific and actionable
- Highlight potential bugs or issues that need to be addressed
- Provide concise code examples for suggested improvements based on official library documentation
- Briefly explain the reasoning, citing documentation when applicable
```
