# Cursor Rules Templates

This project is used to organize and collect Cursor rule files from different projects, providing rule support for multiple programming languages and frameworks.

## Project Overview

Cursor is an AI-assisted programming tool that uses rule files to guide its behavior. The goal of this project is to collect, organize, and standardize these rule files so that developers can make more effective use of Cursor in their development work.

Reference articles and tutorials:

[Cursor Rules Advanced Guide: Building Enterprise-Level Multi-Language Development Standards](https://mp.weixin.qq.com/s/rfanrMtMMuyUTwsDYmlxSg)

[Cursor Rules Best Practices Summary](https://mp.weixin.qq.com/s/-J_LwfwH9rmFy4dzEy0RXg)


## Currently Supported Rule Types

### [General Rules](./common/README.md)
- **General programming rules**
- **Git-related rules**
- **Git Flow workflow rules**
- **Documentation writing rules**

### [Programming Languages](./languages/README.md)
- **Python**
- **Java**
- **TypeScript**
- **Golang**
- **C++**
- **Markdown**
- **Database**

### [Web Frameworks](./frameworks/README.md)
#### Frontend
- **React**
- **Vue.js**
- **Next.js**
- **Svelte**
- **Tailwind CSS**

#### Backend
- **Django**
- **Flask**
- **FastAPI**
- **Express.js**
- **NestJS**

#### Mobile Development Frameworks
- **React Native**
- **Flutter**
- **SwiftUI**

## Features

- Collect Cursor rule files from different projects
- Classify and organize rule files
- Provide standardized rule templates
- Facilitate sharing and reuse of rules across projects

## Usage

1. Clone this repository
2. Browse the rules for the relevant language and framework
3. Apply the applicable rules to your project
4. Contribute your own rules back to the community

## Project Structure

```
cursor-rules/
├── common/              # General rules
│   ├── general.mdc      # General programming rules
│   ├── git.mdc          # Git-related rules
│   ├── gitflow.mdc      # Git Flow workflow rules
│   ├── document.mdc     # Documentation writing rules
│   └── samples/         # Sample implementations
├── languages/           # Language-specific rules
│   ├── python.mdc       # Python rules
│   ├── java.mdc         # Java rules
│   ├── typescript.mdc   # TypeScript rules
│   ├── golang.mdc       # Go rules
│   ├── cpp.mdc          # C++ rules
│   ├── markdown.mdc     # Markdown formatting rules
│   └── database.mdc     # Database and SQL rules
├── frameworks/          # Framework-related rules
│   ├── django.mdc       # Django rules
│   ├── flask.mdc        # Flask rules
│   ├── fastapi.mdc      # FastAPI rules
│   ├── node-express.mdc # Express.js rules
│   ├── typescript-nestjs.mdc # NestJS rules
│   ├── react.mdc        # React rules
│   ├── vuejs.mdc        # Vue.js rules
│   ├── nextjs.mdc       # Next.js rules
│   ├── svelte.mdc       # Svelte rules
│   ├── tailwind.mdc     # Tailwind CSS rules
│   ├── flutter.mdc      # Flutter rules
│   ├── react-native.mdc # React Native rules
│   ├── react-native-expo.mdc # React Native with Expo rules
│   └── swiftui.mdc      # SwiftUI rules
```

## Contribution Guide

Pull Requests are welcome to share your Cursor rules. Please ensure your rule files follow the project's naming conventions and structure. Rules can be in Markdown (.mdc) or JSON format.

## License

MIT
