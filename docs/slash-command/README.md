---
description: A comprehensive guide to creating custom slash commands for Claude Code and Cursor IDE.
---

# Custom Slash Commands

A comprehensive guide to creating custom slash commands for Claude Code and Cursor IDE.

## Claude Code Custom Slash Commands

Custom slash commands in Claude Code are reusable prompts stored as Markdown files that you can trigger with a simple `/command-name` syntax.

### Command Types & Locations

**Project Commands** (`.claude/commands/`)
- Stored in your repository and shared with your team
- Appear with `(project)` label in `/help`
- Checked into git for team collaboration

```bash
mkdir -p .claude/commands
```

**Personal Commands** (`~/.claude/commands/`)
- Available across all your projects
- Appear with `(user)` label in `/help`
- Personal workflow shortcuts

```bash
mkdir -p ~/.claude/commands
```

### Creating Basic Commands

Simply create a Markdown file - the filename becomes the command name:

```bash
# Example: Create /optimize command
echo "Analyze this code for performance issues and suggest optimizations:" > .claude/commands/optimize.md

# Example: Create /security-review command
mkdir -p ~/.claude/commands
echo "Review this code for security vulnerabilities:" > ~/.claude/commands/security-review.md
```

### Using Arguments

#### Single Argument with `$ARGUMENTS`

The `$ARGUMENTS` placeholder captures all arguments passed to the command as a single string:

```markdown
# Review Code
Review this file: $ARGUMENTS with focus on security and performance
```

**Usage:** `/review-code src/auth.js` → captures `"src/auth.js"`

#### Multiple Arguments with Positional Variables

Use `$1`, `$2`, `$3`, etc. for positional arguments:

```markdown
---
argument-hint: [pr-number] [priority] [assignee]
description: Review pull request
---

# Review Pull Request

Review PR #$1 with priority $2 and assign to $3.

## Focus Areas
- Security vulnerabilities
- Performance bottlenecks
- Code style consistency
```

**Usage:** `/review-pr 456 high john@example.com`
- `$1` = `456`
- `$2` = `high`
- `$3` = `john@example.com`

**Note:** Array-style access like `$ARGUMENTS[0]` is not currently supported.

### Organizing with Namespaces

Organize commands in subdirectories to create namespaced commands:

```
.claude/commands/
├── dev/
│   ├── code-review.md      → /project:dev:code-review
│   └── refactor.md          → /project:dev:refactor
├── test/
│   ├── generate.md          → /project:test:generate
│   └── coverage.md          → /project:test:coverage
└── deploy/
    └── prepare-release.md   → /project:deploy:prepare-release
```

### Frontmatter Configuration

Add YAML frontmatter to customize command behavior:

```markdown
---
allowed-tools: Bash(git add:*), Bash(git status:*), Bash(git commit:*)
argument-hint: [message]
description: Create a git commit with conventional commit format
model: claude-3-5-haiku-20241022
disable-model-invocation: true
---

# Git Commit

Create a git commit with message: $ARGUMENTS

## Steps
1. Run `git status` to see all changes
2. Stage all changes with `git add -A`
3. Create commit with message: $ARGUMENTS
4. Follow conventional commit format (feat:, fix:, docs:, etc.)
```

**Frontmatter Options:**
- `description`: Shows in `/help` and provides context to Claude
- `argument-hint`: Displays expected arguments format
- `allowed-tools`: Restricts which tools the command can use
- `model`: Specifies which Claude model to use
- `disable-model-invocation`: Prevents Claude from auto-invoking the command

### Natural Language Triggers

Reference commands in your `CLAUDE.md` to use natural language:

```markdown
## Work Keywords

- **"commit my changes"**: Execute `/commit` command
- **"review this code"**: Execute `/dev:code-review` command
- **"run tests"**: Execute `/test:generate` command
```

This allows you to say "commit my changes" and Claude will automatically execute the `/commit` command.

---

## Cursor Custom Commands

Cursor provides its own custom command system, stored separately from Claude Code commands.

### Command Location

Cursor commands are stored in `.cursor/commands/` directory:

```bash
mkdir -p .cursor/commands
```

Commands are stored in your project repository and shared with your team through git.

### Creating Cursor Commands

Create Markdown files in `.cursor/commands/` directory. The filename becomes the command name:

```markdown
# Generate API Documentation

Create comprehensive API documentation for the current code.

## Objective

Generate complete API documentation that can be used by other developers and integrated into our documentation site.

## Requirements

- Document all endpoints with descriptions and HTTP methods
- Include request/response schemas with examples
- Document authentication requirements
- List all error codes and their meanings
- Include rate limiting information
- Provide code examples in multiple languages

## Output Format

Format the documentation as an OpenAPI/Swagger specification that can be imported into our API documentation tools.

## Additional Context

Follow our existing documentation style guide and ensure consistency with other API endpoints in the system.
```

### Using Commands in Cursor

1. Type `/` in Cursor's Agent or Chat input
2. Select the command from the dropdown menu
3. The command prompt will be inserted and executed

**Tips:**
- Use clear, descriptive filenames
- Include detailed requirements in the command
- Specify expected output format
- Add context about project standards

### Cursor Rules for Slash Commands

You can also create slash command shortcuts using Cursor's Rules feature:

**Location:** Settings → Rules or `.cursor/rules/project.mdc`

```markdown
## Slash Commands

When I type `/s <term>`, use the codebase_search tool to search for the exact term across the entire codebase.

When I type `/l`, use the edit_file tool to gather all the learnings from this conversation and update the sidebar UI documentation.

When I type `/c`, use the run_terminal_command tool to create a git commit based on this conversation. Use conventional commit format (feat:, fix:, refactor:, chore:, etc.).
```

This approach uses Cursor's Rules system to map simple shortcuts to specific tool invocations.

### Cursor & Claude Code Integration

Cursor can work with Claude Code through the Claude Code extension:

1. **Claude Code Extension**: Install the Claude Code extension in Cursor
2. **Launch Options**: Use `Cmd+Esc` (Mac) or `Ctrl+Esc` (Windows/Linux) to open Claude Code in Cursor
3. **Command Locations**: 
   - Cursor reads commands from `.cursor/commands/`
   - Claude Code reads commands from `.claude/commands/` and `~/.claude/commands/`

**Note:** While Cursor has Claude Code integration, each tool maintains its own command directories. For maximum compatibility:
- Store project-specific Cursor commands in `.cursor/commands/`
- Store Claude Code commands in `.claude/commands/`
- Consider duplicating critical commands in both locations if your team uses both tools

---

## Best Practices

### General Guidelines

1. **Use Descriptive Names**: Make filenames reflect the command's purpose
   - ✅ `generate-api-docs.md`
   - ❌ `gad.md`

2. **Add Descriptions**: Always include frontmatter with clear descriptions
   ```markdown
   ---
   description: Generate comprehensive API documentation with examples
   ---
   ```

3. **Structure Commands Clearly**: Use headers and lists for readability
   ```markdown
   ## Steps
   1. First step
   2. Second step
   
   ## Requirements
   - Requirement 1
   - Requirement 2
   ```

4. **Include Examples**: Show expected inputs and outputs
   ```markdown
   ## Example Usage
   
   Input: `/generate-component Button primary`
   
   Expected Output:
   - Button.tsx component file
   - Button.test.tsx test file
   - Button.stories.tsx Storybook file
   ```

5. **Version Control**: Check commands into git for team sharing
   ```bash
   git add .claude/commands/
   git add .cursor/commands/
   git commit -m "chore: add custom slash commands"
   ```

### Performance Tips

1. **Reduce Token Usage**: Extract fixed workflows from `CLAUDE.md` into commands
   - Can reduce token consumption by 20% or more
   - Commands are only loaded when needed

2. **Reusable Patterns**: Create commands for repetitive tasks
   - Code reviews
   - Commit message generation
   - Test generation
   - Documentation updates

3. **Team Standardization**: Share commands via git
   - Ensures consistent workflows
   - New team members get instant access
   - Easy to update and maintain


**By Feature:**
```
.claude/commands/
├── api/
├── ui/
├── database/
└── deployment/
```

**By Role:**
```
.claude/commands/
├── frontend/
├── backend/
├── devops/
└── testing/
```

**By Task Type:**
```
.claude/commands/
├── create/
├── review/
├── test/
└── deploy/
```

---

## Example Commands

This repository includes ready-to-use example commands in the [`docs/slash-command/commands/`](commands/) directory:

- [`commit.md`](commands/commit.md) - Create conventional commits with all changes
- [`dev/create-component.md`](commands/dev/create-component.md) - Generate React components with tests and stories
- [`security-audit.md`](commands/security-audit.md) - Perform comprehensive security audits
- [`fix-github-issue.md`](commands/fix-github-issue.md) - Automatically fix GitHub issues
- [`docs/generate-readme.md`](commands/docs/generate-readme.md) - Generate or update README documentation

To use these commands in your project, copy them to your `.claude/commands/` directory or use them as templates for creating your own custom commands.

### Creating Commands from Prompts

The prompts in the [`docs/prompt-library/`](../prompt-library/) can be easily converted into custom slash commands. Simply:

1. Create a new `.md` file in `.claude/commands/` (or `~/.claude/commands/` for personal commands)
2. Copy the prompt content into the file
3. Add frontmatter with `description` and `argument-hint` if needed
4. Use `$ARGUMENTS`, `$1`, `$2`, etc. for dynamic arguments

This allows you to quickly access frequently-used prompts with a simple `/command-name` instead of copying and pasting.

---

## Additional Resources

### Claude Code
- [Official Slash Commands Documentation](https://docs.claude.com/en/docs/claude-code/slash-commands)
- [Claude Code Best Practices](https://www.anthropic.com/engineering/claude-code-best-practices)

### Cursor
- [Cursor Commands Documentation](https://cursor.com/docs/agent/chat/commands)
- [Cursor Agent Documentation](https://cursor.com/docs/agent)

### Community Resources
- [Claude Command Suite](https://github.com/qdhenry/Claude-Command-Suite) - 148+ production-ready commands
- [Awesome Claude Code](https://github.com/hesreallyhim/awesome-claude-code) - Curated list of resources
- [Cursor Commands Repository](https://github.com/hamzafer/cursor-commands) - Cursor command examples
