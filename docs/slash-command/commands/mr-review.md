---
argument-hint: [mr-number]
description: Structured prompt for conducting thorough merge request reviews with quality and security checks.
---

Please help me review merge request #[$1] of the current project.

Make use of MCP tools from `gitlab-mr-mcp` MCP server:
- DO NOT call `get-projects`, instead getting project id from `general.mdc` 
- Call `get_merge_request_details`, `get_merge_request_diff`, `get_merge_request_comments` to fetch merge request details
- Call `add_merge_request_comment` and `add_merge_request_diff_comment` to add comments to the merge request

First, analyze the file types that have been changed in this merge request and load the appropriate Cursor rules based on file types.

Apply the appropriate rules when reviewing each file and ensure your feedback aligns with the project's established conventions as defined in these ruleset files.

## Coding Guidelines
Please follow these guidelines for the review:

1. Code Quality & Standards:
   - Follow language-specific best practices according to the Cursor rules
   - Ensure proper error handling and type safety where applicable
   - Check for code duplication and unnecessary complexity
   - Verify naming conventions and code formatting based on project standards
   - Look for potential memory leaks or performance issues
   - Ensure architecture principles are followed (e.g., hexagonal architecture for TypeScript)

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
Add comments directly to the merge request:
1. General comment that start with overall summary, followed by all the findings.
2. Detailed inline comments on specific code sections that expect code changes
3. DO NOT include a Final Summary comment

For each inline comment, please:
- Reference the specific Cursor rule that applies, if any
- Make it clear the comment it is made by Cursor IDE
- Include file names and line numbers
- The inline commment should be inserted right after the code referring to (line number + 1)
- Be specific and actionable
- Skip comments only about documentation changes
- Highlgiht any potential bugs or issues that need to be addressed
- Provide code examples for suggested improvements
- Explain the reasoning behind each suggestion