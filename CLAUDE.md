# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is the **AI SDLC Playbook** - a comprehensive documentation site built with MkDocs that provides practical guidance for integrating AI tools and practices into Software Development Lifecycle (SDLC). The site includes IDE rules, MCP server resources, AI development workflows, and a prompt library for AI-assisted development.

## Architecture

- **Documentation Site**: Built with MkDocs Material theme
- **Content Organization**:
  - `docs/ide-rules/` - Rules and guidelines for AI-powered IDEs (Cursor, etc.)
  - `docs/mcp-server/` - Model Control Protocol server resources
  - `docs/workflow/` - AI development workflows and methodologies
  - `docs/prompt-library/` - Curated AI prompts for development tasks
- **Configuration**: `mkdocs.yml` with Material theme, mermaid2 plugin, and custom styling
- **Deployment**: Automated via GitHub Actions to GitHub Pages

## Common Development Commands

### Setup
```bash
# Create and activate Python virtual environment
python -m venv .venv
source .venv/bin/activate  # On Windows: .venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt
```

### Local Development
```bash
# Start local development server (with hot reload)
mkdocs serve --dev-addr=0.0.0.0:8000

# Build static site
mkdocs build

# Build with clean output directory
mkdocs build --clean
```

### Dependency Management
```bash
# Update requirements.txt from requirements.in
pip-compile requirements.in
```

## Content Guidelines

Follow the Cursor rules defined in `.cursor/rules/`:

- **Markdown Formatting**: Use ATX-style headings, specify language in code blocks, use `-` for lists, maintain proper spacing
- **Lists**: Include new line before nested sub-lists, use 4-space indentation
- **General**: Think step by step, make targeted edits, validate changes

## Site Structure

Key directories:
- `docs/` - All documentation content
- `site/` - Generated static site (build output)
- `.overrides/` - Theme customizations
- `docs/assets/`, `docs/img/` - Static assets and images
- `docs/stylesheets/` - Custom CSS

## Deployment

The site auto-deploys to GitHub Pages via `.github/workflows/publish.yml` when:
- Changes are pushed to main branch
- Manual workflow trigger from GitHub Actions tab

Published at: https://kevinlin.github.io/ai-sdlc-playbook