# AI SDLC Playbook

This playbook provides guidance on best practices for integrating AI into the Software Development Lifecycle (SDLC), specifically tailored to Zuhlke's needs and challenges. It serves as a living document, continuously updated to reflect emerging practices and lessons learned.

## Table of Contents
1. [AI Development Workflow](docs/workflow/README.md)
	1. [Getting Started](docs/workflow/workflow-getting-started.md)
	2. [Project Setup](docs/workflow/workflow-project-setup.md)
	3. Feature Development Lifecycle
		1. [Product Requirements](docs/workflow/workflow-product-requirements.md)
		2. [Development](docs/workflow/workflow-development.md)
		3. [Testing](docs/workflow/workflow-testing.md)
		4. [Refactoring](docs/workflow/workflow-refactoring.md)
		5. [Documentation](docs/workflow/workflow-documentation.md)
	4. [Learning with AI](docs/workflow/workflow-learning.md)
1. [Cursor Rules](docs/cursor-rules/README.md)
    1. [Common Rules](docs/cursor-rules/common/README.md)
	2. [Language Rules](docs/cursor-rules/languages/README.md)
	3. [Framework Rules](docs/cursor-rules/frameworks/README.md)
1. [Prompt Library](docs/prompt-library/README.md)
    1. [Prompting Guidance](docs/prompt-library/prompting-guidance.md)

## Site Publish

### Setting up Python Virtual Environment

```bash
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

### Local Development

Start a local development server:

```bash
mkdocs serve --dev-addr=0.0.0.0:8000
```

### Building the Site

Build the static site:

```bash
mkdocs build
```

### GitHub Actions Deployment

This repository includes a GitHub Actions workflow that automatically builds and deploys the site to GitHub Pages when:
- Changes are pushed to the main branch
- The workflow is manually triggered from the Actions tab

The workflow configuration is located in `.github/workflows/publish.yml` and uses GitHub's official Pages deployment actions with the following steps:
1. Checkout the source code
2. Set up Python environment
3. Install dependencies and build the site
4. Upload the generated files as an artifact
5. Deploy to GitHub Pages

To manually trigger a deployment, go to the Actions tab in the GitHub repository and run the "Build & Publish site to GitHub Pages" workflow.

The site is published at: https://kevinlin.github.io/ai-sdlc-playbook