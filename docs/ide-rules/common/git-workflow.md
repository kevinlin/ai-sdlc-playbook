---
description: Git workflow best practices covering branching strategies, commit conventions, and collaborative development patterns.
---

# Git Workflow Guidelines

## IDE Configuration Headers

### For Cursor IDE

To create a new Cursor Rule:

1. Enter the name as `git-workflow`
2. Copy & paste the following header and rule content below:

```markdown
---
description: Git Workflow Guidelines
globs: **/*
alwaysApply: false
---
```

### For Kiro IDE

To create a new Kiro Steering Document:

1. Create a file named `git-workflow.md` in `.kiro/steering/`
2. Copy & paste the following header and rule content below:

```markdown
---
inclusion: always
---
```

For more information about IDE rules, visit:
- [Cursor Project Rules](https://docs.cursor.com/context/rules#project-rules)
- [Kiro Steering Documents](https://github.com/kirolabs/kiro)

## Rule Content

```markdown
# Git Workflow Guidelines

## General Git Principles

### Important Safety Rules
- **Critical**: Do not commit git code automatically unless explicitly instructed
- Ensure all tests pass before committing
- Keep commit messages concise and clear, describing the changes
- Avoid large commits; break changes into small, related commits whenever possible
- No direct commits to protected branches (main, develop)
- All changes must go through Pull Requests for code review

## Commit Guidelines

### Commit Message Format
Git commit template: `<type>(<scope>): <subject>`

**Requirements:**
1. Include a space after the colon (:)
2. Use sentence case for subject line
3. Keep subject line under 50 characters when possible
4. Use imperative mood ("Add feature" not "Added feature")

### Commit Types
The allowed values for type are:

- **feat**: New feature
- **fix**: Bug fix
- **docs**: Documentation/comment changes
- **style**: Code formatting (changes that do not affect code execution)
- **refactor**: Code refactoring (not adding new features or fixing bugs)
- **perf**: Performance optimization
- **test**: Add or modify tests
- **chore**: Changes to build process or auxiliary tools
- **revert**: Revert previous commit
- **build**: Build system changes

### Multi-point Commits
If the subject describes more than two points, use a bullet list for details:

```
feat(web): implement email verification workflow

- Add email verification token generation service
- Create verification email template with dynamic links
- Add API endpoint for token validation
- Update user model with verification status field
```

## GitFlow Workflow

### Main Branches

#### main (or master)
- Contains production-ready code
- Never commit directly to main
- Only accepts merges from:
  - hotfix/* branches
  - release/* branches
- Must be tagged with version number after each merge
- Always stable and ready for release

#### develop
- Main development branch
- Contains latest delivered development changes
- Source branch for feature branches
- Target branch for feature merges
- Never commit directly to develop

### Supporting Branches

#### feature/*
- **Branch from**: develop
- **Merge back into**: develop
- **Naming convention**: feature/[issue-id]-descriptive-name
- **Example**: feature/123-user-authentication
- Must be up-to-date with develop before creating PR
- Delete after successful merge
- For developing new features and enhancements

#### release/*
- **Branch from**: develop
- **Merge back into**: main AND develop
- **Naming convention**: release/vX.Y.Z
- **Example**: release/v1.2.0
- Only bug fixes, documentation, and release-oriented tasks allowed
- No new features permitted
- Delete after merge
- Used for preparing releases

#### hotfix/*
- **Branch from**: main
- **Merge back into**: main AND develop
- **Naming convention**: hotfix/vX.Y.Z
- **Example**: hotfix/v1.2.1
- Only for urgent production fixes
- Delete after merge
- Used for critical bug fixes in production

### Branch Naming Conventions

| Branch Type | Naming Format           | Example                      | Purpose                    |
|-------------|------------------------|------------------------------|----------------------------|
| Feature     | feature/[description]   | feature/user-auth            | New features               |
| Bugfix      | fix/[issueID]-[desc]    | fix/issue-42-login-crash     | Bug fixes in development   |
| Release     | release/[version]       | release/v2.1.0               | Release preparation        |
| Hotfix      | hotfix/[version]-[desc] | hotfix/v2.0.1-payment-fix    | Critical production fixes  |

## Pull Request Rules

1. **Required for all changes**: All code changes must go through Pull Requests
2. **Minimum approvals**: At least 1 reviewer approval required
3. **CI requirements**: All automated checks must pass
4. **Up-to-date requirement**: Branch must be current with target branch
5. **Clean up**: Delete feature branch after successful merge
6. **Review focus**: Code quality, security, and adherence to standards

## Branch Protection Rules

### Protected Branches (main & develop)
- Require pull request reviews before merging
- Require status checks to pass before merging
- Require branches to be up to date before merging
- Include administrators in branch protection restrictions
- Prevent force pushes
- Prevent branch deletion

## Release Process

1. **Create release branch** from develop
   ```bash
   git checkout develop
   git checkout -b release/v1.2.0
   ```

2. **Prepare release**
   - Bump version numbers in relevant files
   - Update CHANGELOG.md
   - Fix any release-specific issues (no new features)

3. **Create Pull Request** to main
   - Review all changes thoroughly
   - Ensure all tests pass

4. **After merge to main**
   - Tag the release
   ```bash
   git tag -a v1.2.0 -m "Release version 1.2.0"
   git push origin v1.2.0
   ```
   - Merge release branch back to develop
   - Delete release branch

## Hotfix Process

1. **Create hotfix branch** from main
   ```bash
   git checkout main
   git checkout -b hotfix/v1.2.1-critical-fix
   ```

2. **Fix the critical issue**
   - Keep changes minimal and focused
   - Bump patch version number

3. **Create Pull Request** to main
   - Expedited review for critical fixes
   - Ensure fix doesn't break existing functionality

4. **After merge to main**
   - Tag the hotfix release
   ```bash
   git tag -a v1.2.1 -m "Hotfix version 1.2.1"
   git push origin v1.2.1
   ```
   - Merge hotfix branch back to develop
   - Delete hotfix branch

## Version Control

### Semantic Versioning (SemVer)
Follow semantic versioning principles for all releases:

- **MAJOR** (X.0.0): Incompatible API changes or breaking changes
- **MINOR** (X.Y.0): Backwards-compatible new functionality
- **PATCH** (X.Y.Z): Backwards-compatible bug fixes

### Examples
- `1.0.0` → `1.0.1` (bug fix)
- `1.0.1` → `1.1.0` (new feature, backwards compatible)
- `1.1.0` → `2.0.0` (breaking change)

### Pre-release Versions
- Use suffixes for pre-release versions: `1.2.0-beta.1`, `1.2.0-rc.1`
- Always test pre-release versions thoroughly before final release
``` 