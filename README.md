# AI SDLC Playbook

A comprehensive guide for integrating AI tools and practices into the Software Development Lifecycle (SDLC), specifically designed for development teams looking to enhance their productivity and code quality through AI assistance.

## About

This playbook provides practical guidance, rules, workflows, and prompts for effectively using AI-powered IDEs like Cursor, Kiro, and other AI development assistants. It's tailored for teams who want to adopt AI-driven development practices while maintaining high standards of code quality, security, and maintainability.

**Target Audience**: Software developers, development teams, technical leads, and organizations looking to integrate AI into their development workflow.

## Quick Start

1. **Browse the Documentation**: Visit the [complete documentation](docs/README.md) for detailed guidance
2. **Choose Your Focus Area**:
   - New to AI development? Start with [Getting Started](docs/workflow/01-getting-started.md)
   - Setting up AI IDE rules? Check [IDE Rules](docs/ide-rules/README.md)
   - Looking for prompts? Explore the [Prompt Library](docs/prompt-library/README.md)
3. **Follow the Workflow**: Implement the [AI Development Workflow](docs/workflow/README.md) in your projects

## What's Included

- **[IDE Rules](docs/ide-rules/README.md)** - Rules and guidelines for AI-powered IDEs to improve AI assistance
- **[MCP Server](docs/mcp-server/README.md)** - Model Control Protocol server resources for enhanced AI capabilities
- **[AI Development Workflow](docs/workflow/README.md)** - Step-by-step workflow for AI-assisted development
- **[Prompt Library](docs/prompt-library/README.md)** - Curated collection of effective AI prompts for development tasks

## Usage Examples

- **Setting up a new project**: Follow the [Project Setup](docs/workflow/02-project-setup.md) guide
- **Implementing a feature**: Choose from [3 Development Workflows](docs/workflow/README.md#choose-your-development-workflow) based on your project needs
- **Code review**: Apply prompts from [Development](docs/prompt-library/README.md#development) section
- **Documentation**: Use [Documentation prompts](docs/prompt-library/README.md#documentation) for automated docs

## Live Documentation

The complete documentation is available at: **https://kevinlin.github.io/ai-sdlc-playbook**

## Contributing

We welcome contributions! Please:

1. Fork the repository
2. Create a feature branch
3. Make your changes following our [Markdown Guidelines](docs/ide-rules/languages/markdown.md)
4. Submit a pull request

For major changes, please open an issue first to discuss what you would like to change.

## 📄 License

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details.

**Attribution**: Large sections of this playbook were adapted from the [DEFRA AI SDLC Playbook](https://github.com/DEFRA/defra-ai-sdlc) © Crown copyright (2023) Department for Environment, Food & Rural Affairs, originally released under the [Open Government Licence v3.0](http://www.nationalarchives.gov.uk/doc/open-government-licence/version/3/).

---

## 🔧 Development & Site Publishing

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