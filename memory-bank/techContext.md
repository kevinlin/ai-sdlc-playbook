# Tech Context: AI SDLC Playbook

## Technologies Used
- **Documentation Generator**: MkDocs (Python-based static site generator)
- **Theme**: Material for MkDocs (modern, responsive design)
- **Markup Language**: Markdown with extensions
- **Deployment Platform**: GitHub Pages
- **CI/CD**: GitHub Actions
- **Version Control**: Git/GitHub
- **Python Environment**: Virtual environment with requirements.txt
- **Diagram Support**: Mermaid (for flowcharts and diagrams)

## Development Setup
```bash
# Virtual environment setup
python -m venv .venv
source .venv/bin/activate  # On macOS/Linux
pip install -r requirements.txt

# Local development server
mkdocs serve --dev-addr=0.0.0.0:8000

# Build static site
mkdocs build
```

**Requirements**: Python 3.x, pip, virtual environment support
**Local Testing**: http://localhost:8000 for development preview
**File Watching**: MkDocs automatically reloads on file changes during development

## Technical Constraints
- **GitHub Pages Limitations**: Static site only, no server-side processing
- **MkDocs Constraints**: Limited to supported markdown extensions and themes
- **Build Environment**: Must be compatible with GitHub Actions Ubuntu runners
- **File Size**: Reasonable limits for documentation assets and images
- **Browser Compatibility**: Must work across modern browsers
- **Mobile Responsiveness**: Documentation must be accessible on mobile devices

## Dependencies
**Core Dependencies** (from requirements.txt):
- `mkdocs`: Core documentation generator
- `mkdocs-material`: Material theme for modern UI
- `mkdocs-awesome-nav`: Enhanced navigation capabilities
- `mkdocs-mermaid2-plugin`: Mermaid diagram support

**Development Dependencies**:
- Python 3.x runtime
- pip package manager
- Git for version control
- Text editor/IDE for markdown editing

## Tool Usage Patterns
- **Content Creation**: Write in Markdown using standard editors
- **Local Testing**: Use `mkdocs serve` for immediate preview
- **Version Control**: Standard Git workflow with feature branches
- **Deployment**: Automated via GitHub Actions on push to main
- **Memory Bank**: Separate tooling for AI assistant context management
- **Asset Management**: Direct file placement in appropriate directories
- **Configuration**: YAML-based configuration in mkdocs.yml 