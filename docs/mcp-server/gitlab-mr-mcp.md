---
description: MCP server implementation providing GitLab merge request integration for AI-powered development workflows.
---

# GitLab Merge Request MCP Server

## Overview

The GitLab Merge Request MCP Server enables AI agents to seamlessly interact with GitLab repositories, manage merge requests, review code, and post comments directly from your AI assistant. This powerful integration brings GitLab's collaborative features into your AI-powered development workflow.

## What is GitLab MR MCP?

GitLab MR MCP is an implementation of the Model Context Protocol (MCP) that provides a bridge between AI assistants and GitLab's API. It allows you to perform GitLab operations without leaving your development environment, making code review and project management more efficient.

## Key Features

- **Project Management**: List and access GitLab projects with your token permissions
- **Merge Request Operations**: Create, view, and manage merge requests programmatically
- **Code Review**: Add comments to specific lines in code diffs
- **Issue Tracking**: Fetch and manage GitLab issues
- **Automated Workflows**: Integrate GitLab operations into AI-assisted development processes

## Installation

### Using npx (Recommended)

The easiest way to use GitLab MR MCP is with npx, which always gets the latest version:

```bash
# Set required environment variables
export MR_MCP_GITLAB_HOST="your_gitlab_host"
export MR_MCP_GITLAB_TOKEN="your_gitlab_token"

# Run directly with npx
npx gitlab-mr-mcp@0.1.0
```

### Manual Installation

For development or customization:

```bash
# Clone the repository
git clone https://github.com/kevinlin/gitlab-mr-mcp
cd gitlab-mr-mcp

# Install dependencies
npm install

# Run the server
npm start
```

## Configuration

### Prerequisites

Before using GitLab MR MCP, ensure you have:

- **Node.js** installed on your system
- **GitLab access token** with API permissions
- **GitLab project access** for the repositories you want to manage

### Environment Variables

The server requires these environment variables:

- `MR_MCP_GITLAB_HOST`: Your GitLab instance URL (e.g., `https://gitlab.com`)
- `MR_MCP_GITLAB_TOKEN`: Your GitLab personal access token with `api` and `read_api` scopes

Optional filtering variables:

- `MR_MCP_MIN_ACCESS_LEVEL`: Minimum access level for projects (see [GitLab access levels](https://docs.gitlab.com/api/access_requests/#valid-access-levels))
- `MR_MCP_PROJECT_SEARCH_TERM`: Search term to filter projects by name or path

### Cursor Integration

Add the following configuration to your Cursor MCP settings:

#### Using npx (Recommended)

```json
{
  "mcpServers": {
    "gitlab-mr-mcp": {
      "command": "npx",
      "args": ["gitlab-mr-mcp@0.1.0"],
      "env": {
        "MR_MCP_GITLAB_HOST": "your_gitlab_host",
        "MR_MCP_GITLAB_TOKEN": "your_gitlab_token"
      }
    }
  }
}
```

#### Using Local Installation

```json
{
  "mcpServers": {
    "gitlab-mr-mcp": {
      "command": "node",
      "args": ["/path/to/gitlab-mr-mcp/index.js"],
      "env": {
        "MR_MCP_GITLAB_HOST": "your_gitlab_host",
        "MR_MCP_GITLAB_TOKEN": "your_gitlab_token"
      }
    }
  }
}
```

## Available Tools

GitLab MR MCP provides comprehensive tools for GitLab integration:

### Project Management

- **`get_projects`**
  - Gets a list of GitLab projects accessible with your token
  - Supports filtering by access level and search terms
  - Returns project IDs, names, descriptions, and URLs

### Merge Request Operations

- **`list_open_merge_requests`**
  - Lists all open merge requests in a specified project
  - Provides summary information for quick overview
  - Essential for code review workflows

- **`get_merge_request_details`**
  - Gets detailed information about a specific merge request
  - Includes title, description, author, reviewers, and status
  - Provides comprehensive context for review decisions

- **`get_merge_request_diff`**
  - Retrieves the complete diff for a merge request
  - Shows all file changes with line-by-line differences
  - Critical for understanding code changes

- **`set_merge_request_title`**
  - Updates the title of a merge request
  - Useful for maintaining clear, descriptive titles

- **`set_merge_request_description`**
  - Updates the description of a merge request
  - Enables detailed documentation of changes

### Code Review and Comments

- **`get_merge_request_comments`**
  - Retrieves all comments from a merge request
  - Includes both general discussion notes and diff-specific comments
  - Provides complete review conversation history

- **`add_merge_request_comment`**
  - Adds a general comment to a merge request
  - Perfect for overall feedback and discussion

- **`add_merge_request_diff_comment`**
  - Adds a comment to a specific line in a file within a merge request
  - Enables precise, line-level code review feedback
  - Supports threaded discussions on specific code changes

### Issue Management

- **`get_issue_details`**
  - Gets detailed information about a specific GitLab issue
  - Provides context for issue-related development work

## Use Cases and Workflows

### Code Review Automation

```bash
# Example workflow for automated code review
1. List open merge requests in a project
2. Get detailed information about a specific MR
3. Retrieve the diff to understand changes
4. Add line-specific comments for issues found
5. Add general feedback comment
```

### Project Management Integration

```bash
# Example workflow for project oversight
1. Get list of accessible projects
2. Check open merge requests across projects
3. Review issue details for context
4. Provide feedback and guidance through comments
```

### AI-Assisted Development

The MCP server enables AI assistants to:

- **Automatically review code** by analyzing diffs and suggesting improvements
- **Manage merge request workflows** by updating titles, descriptions, and adding comments
- **Provide project insights** by analyzing open merge requests and issues
- **Facilitate team communication** by posting structured feedback and updates

## Security and Permissions

### Token Permissions

Your GitLab token should have the following scopes:

- **`api`**: Full API access for creating and modifying resources
- **`read_api`**: Read access to API resources for fetching data

### Access Control

The server respects GitLab's built-in access control:

- Only projects accessible to your token will be available
- Comment and modification permissions follow your GitLab role
- Use `MR_MCP_MIN_ACCESS_LEVEL` to further restrict access

### Best Practices

1. **Use dedicated tokens**: Create a specific token for MCP integration
2. **Limit scope**: Only grant necessary permissions to your token
3. **Rotate regularly**: Update tokens periodically for security
4. **Monitor usage**: Review token activity in GitLab's access logs

## Troubleshooting

### Common Issues and Solutions

#### Connection Problems

1. **Check MCP client logs first**: Enable debug logging in your MCP client to see detailed error messages and connection status
2. **Verify environment variables**: Ensure `MR_MCP_GITLAB_HOST` and `MR_MCP_GITLAB_TOKEN` are correctly set
3. **Test GitLab connectivity**: Verify your GitLab instance is accessible

#### Permission Errors (403 Forbidden)

When encountering permission issues:

1. **Verify token scopes**: Ensure your GitLab token has `api` and `read_api` scopes
2. **Check project access**: Confirm the token user has proper access to the target projects
3. **Validate project IDs**: Ensure you're using correct project IDs from the `get_projects` tool

#### API Rate Limiting

GitLab implements rate limiting for API calls:

1. **Monitor usage**: Be aware of your API call frequency
2. **Implement delays**: Space out rapid successive calls
3. **Check limits**: Review your GitLab instance's rate limit policies

### Debugging Steps

1. **Enable verbose logging** in your MCP client
2. **Test with GitLab API directly** using curl or Postman
3. **Verify token permissions** in GitLab's user settings
4. **Check project visibility** and access levels

## Development and Customization

### Running the Inspector

For development and testing:

```bash
# Set environment variables
export MR_MCP_GITLAB_TOKEN=your_gitlab_token
export MR_MCP_GITLAB_HOST=your_gitlab_host

# Optional: Set filtering variables
export MR_MCP_MIN_ACCESS_LEVEL=30
export MR_MCP_PROJECT_SEARCH_TERM=my-project

# Run the MCP inspector
npx -y @modelcontextprotocol/inspector npm start
```

### Extending Functionality

The server is built with TypeScript and follows MCP best practices:

- **Tool definitions**: Each GitLab operation is implemented as an MCP tool
- **Error handling**: Comprehensive error responses for debugging
- **Type safety**: Full TypeScript support for reliable development

## Related Resources

- [MCP Server Overview](README.md) - General information about MCP servers
- [Spec-driven Dev MCP](spec-driven-dev-mcp.md) - Complementary development workflow tool
- [Memory Bank](memory-bank.md) - Context management for development projects

## Links

- [GitHub Repository](https://github.com/kevinlin/gitlab-mr-mcp)
- [Smithery Badge](https://smithery.ai/server/@kevinlin/gitlab-mr-mcp)
- [GitLab API Documentation](https://docs.gitlab.com/api/)
- [Model Context Protocol](https://modelcontextprotocol.io/)

## License

This project is licensed under the [MIT License](https://github.com/kevinlin/gitlab-mr-mcp/blob/main/LICENSE).