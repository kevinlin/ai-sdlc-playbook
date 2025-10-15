# Documentation Commands

This namespace contains commands for creating and maintaining documentation. These commands help ensure your project is well-documented and accessible to all team members.

## Available Commands

- **create-architecture-documentation.md** - Create comprehensive architecture documentation
- **create-onboarding-guide.md** - Generate onboarding guides for new team members
- **doc-api.md** - Document APIs with examples and specifications
- **generate-api-documentation.md** - Automatically generate API documentation from code
- **generate-readme.md** - Generate or update README documentation
- **migration-guide.md** - Create migration guides for version upgrades
- **troubleshooting-guide.md** - Build troubleshooting guides for common issues

---

## Generate README

**Command**: `/docs:generate-readme [section]`

Generate or update comprehensive README documentation for the current project.

### Usage

```bash
# Generate complete README
/docs:generate-readme

# Update specific section
/docs:generate-readme Installation
/docs:generate-readme Usage
```

### Sections Included

1. **Project Title & Description**
    - Clear, concise project description
    - Key features and benefits
    - Target audience

2. **Installation**
    - Prerequisites
    - Step-by-step installation instructions
    - Common installation issues and solutions

3. **Usage**
    - Basic usage examples
    - Common use cases
    - Code snippets with explanations

4. **Configuration**
    - Environment variables
    - Configuration files
    - Available options

5. **API Documentation** (if applicable)
    - Endpoint descriptions
    - Request/response examples
    - Authentication details

6. **Development**
    - Local setup instructions
    - Running tests
    - Code style guidelines
    - Contribution guidelines

7. **Deployment**
    - Deployment instructions
    - Environment-specific notes
    - CI/CD information

8. **License & Credits**
    - License information
    - Contributors
    - Acknowledgments

### Style Guidelines

The generated README will:

- Use clear, concise language
- Include code examples where helpful
- Use proper Markdown formatting
- Add badges for build status, coverage, etc.
- Include table of contents for long READMEs

### Focus Area

If a section name is provided as an argument, the command will focus on updating or improving that specific section. Otherwise, it generates a complete README from scratch.