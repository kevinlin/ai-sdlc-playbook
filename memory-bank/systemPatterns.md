# System Patterns: AI SDLC Playbook

## System Architecture
The AI SDLC Playbook follows a documentation-centric architecture built on MkDocs:

- **Documentation Source**: Markdown files in `/docs` directory
- **Static Site Generation**: MkDocs with Material theme
- **Deployment**: GitHub Pages with automated CI/CD
- **Memory Bank**: Separate `/memory-bank` directory for AI assistant context
- **Asset Management**: Images and stylesheets in dedicated directories
- **Configuration**: Centralized in `mkdocs.yml`

## Key Technical Decisions
- **MkDocs over alternatives**: Chosen for simplicity, Python ecosystem integration, and GitHub Pages compatibility
- **Material Theme**: Provides professional appearance and good mobile responsiveness
- **Markdown Extensions**: Using pymdownx.superfences for enhanced code blocks and Mermaid diagram support
- **Directory Structure**: Logical separation by content type (cursor-rules, workflow, prompt-library)
- **Version Control**: Git-based workflow with main branch deployment
- **Memory Bank Separation**: Isolated from main docs to avoid conflicts with site generation

## Design Patterns in Use
- **Hierarchical Documentation**: Clear parent-child relationships between documentation sections
- **Template-Based Content**: Consistent structure across similar document types
- **Reference Architecture**: Cross-linking between related documentation sections
- **Modular Organization**: Self-contained sections that can be updated independently
- **Progressive Disclosure**: Information organized from general to specific detail levels

## Component Relationships
- **Main Documentation** (`/docs`) → **Static Site** (GitHub Pages)
- **Memory Bank** (`/memory-bank`) → **AI Context** (Assistant understanding)
- **Configuration** (`mkdocs.yml`) → **Site Generation** (Build process)
- **Assets** (`/docs/img`, `/docs/stylesheets`) → **Site Presentation** (Visual elements)
- **Workflow Files** (`.github/workflows`) → **Deployment** (CI/CD pipeline)

## Critical Implementation Paths
- **Content Creation**: Markdown files → MkDocs processing → Static HTML
- **Deployment Pipeline**: Git push → GitHub Actions → Site build → GitHub Pages
- **Memory Bank Updates**: File modifications → AI context refresh → Improved assistance
- **Documentation Maintenance**: Content updates → Version control → Automated deployment
- **User Journey**: Landing page → Navigation → Specific guidance → Implementation 