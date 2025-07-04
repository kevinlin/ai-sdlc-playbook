# Git Guidelines

To create a new Cursor Rule:

1. Enter the name as `git`
2. Copy & paste the file content from below

For more information, visit the [Project rules](https://docs.cursor.com/context/rules#project-rules).


```markdown
---
description: Git Guidelines
globs: **/*
alwaysApply: false
---

# Git Guidelines

## Important Principles
- **Important**: Do not commit git code automatically unless explicitly instructed
- Ensure all tests pass before committing
- Keep commit messages concise and clear, describing the changes
- Avoid large commits; break changes into small, related commits whenever possible

## Commit Guidelines
Git commit template <type>(<scope>): <subject>, with the following requirements:
1. Note: there is a space after the colon :
2. The allowed values for type are:
- feat: New feature
- fix: Bug fix
- docs: Documentation/comment
- style: Code formatting (changes that do not affect code execution)
- refactor: Refactor/optimization (not adding new features or fixing bugs)
- perf: Performance optimization
- test: Add tests
- chore: Changes to build process or auxiliary tools
- revert: Revert
- build: Build
3. If the subject describes more than two points, use a bullet list for details, each point starting with a dash, with multiple lines. Example:
```
feat(web): implement email verification workflow

- Add email verification token generation service
- Create verification email template with dynamic links
- Add API endpoint for token validation
- Update user model with verification status field
```

## Branch Management
- main/master: Main branch, always stable and ready for release
- develop: Development branch, contains the latest development features
- feature/*: Feature branches, for developing new features
- bugfix/*: Bugfix branches, for fixing bugs
- release/*: Release branches, for preparing releases

**Common Branch Naming Conventions**:

| Branch Type   | Naming Format           | Example                      |
| -------------| ----------------------- | ---------------------------- |
| Feature      | feature/[description]   | feature/user-auth            |
| Bugfix       | fix/[issueID]-[desc]    | fix/issue-42-login-crash     |
| Release      | release/[version]       | release/v2.1.0               |
| Hotfix       | hotfix/[version]-[desc] | hotfix/v2.0.1-payment-fix    |
```