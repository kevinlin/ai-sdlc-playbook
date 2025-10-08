## Two Types of Commands

**Project Commands** (`.claude/commands/`)
- Stored in your repository and shared with your team
- Appear as `(project)` in `/help`
```bash
mkdir -p .claude/commands
```

**Personal Commands** (`~/.claude/commands/`)
- Available across all your projects
- Appear as `(user)` in `/help`
```bash
mkdir -p ~/.claude/commands
```

## Creating a Command

Simply create a Markdown file - the filename becomes the command name:

```bash
# Example: Create /optimize command
echo "Analyze this code for performance issues and suggest optimizations:" > .claude/commands/optimize.md
```

## Using Arguments

Use the special `$ARGUMENTS` keyword to pass parameters:

```markdown
# Fix GitHub Issue

Please analyze and fix GitHub issue: $ARGUMENTS

## Steps
1. Use `gh issue view $ARGUMENTS` to get issue details
2. Understand the problem
3. Search codebase for relevant files
4. Implement necessary changes
...
```

Then invoke: `/project:fix-github-issue 1234`

## Namespacing with Directories

Organize commands in subdirectories to create namespaced commands:

```
.claude/commands/
├── dev/
│   ├── code-review.md    → /project:dev:code-review
│   └── refactor.md       → /project:dev:refactor
└── test/
    └── generate.md       → /project:test:generate
```

## Natural Language Triggers

Reference commands in your `CLAUDE.md` to use natural language:

```markdown
### Work Keywords
- **"commit my changes"**: Execute `/commit` command
- **"review this"**: Execute `/dev:code-review` command
```

This way, you can just say "commit my changes" and Claude will execute the slash command automatically.

## Pro Tips

- Commands reduce token consumption by extracting fixed workflows from your CLAUDE.md files
- Check them into git for team consistency
- Add frontmatter with `description:` field for better context
- Use `disable-model-invocation: true` in frontmatter if you don't want Claude to auto-invoke a command

Want to see real examples? Check out the [Claude Command Suite](https://github.com/qdhenry/Claude-Command-Suite) which has 148+ production-ready commands organized by namespace.