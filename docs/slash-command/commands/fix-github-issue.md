---
argument-hint: [issue-number]
description: Automatically fix a GitHub issue
---

# Fix GitHub Issue

Please analyze and fix GitHub issue: $ARGUMENTS

## Steps

1. Use `gh issue view $ARGUMENTS` to get the issue details
2. Understand the problem described in the issue
3. Search the codebase for relevant files using codebase search
4. Implement the necessary changes to fix the issue
5. Write and run tests to verify the fix
6. Ensure code passes linting and type checking
7. Create a descriptive commit message following conventional commits
8. Push changes and create a PR

## Guidelines

- Always test the fix before committing
- Include the issue number in the commit message
- Update relevant documentation if needed
- Consider edge cases and potential side effects
