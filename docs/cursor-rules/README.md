# Cursor Rules Overview

Cursor is an AI-assisted programming tool that uses rule files to guide its behavior. The goal of this project is to collect, organize, and standardize these rule files so that developers can make more effective use of Cursor in their development work.

## Rule Structure
```mermaid
graph TD
    A[Cursor Rules]
    
    A1[Project-specific Rules]
    A2[General Rules]
    A --> A1
    A --> A2

    A1a[Overview]
    A1b[Project Structure]
    A1 --> A1a
    A1 --> A1b

    A1a1[general.mdc]
    A1a2[important-files.mdc]
    A1a --> A1a1
    A1a --> A1a2

    A1b1[project-structure.mdc]
    A1b2[feature.mdc]
    A1b --> A1b1
    A1b --> A1b2

    A2a[Framework Rules]
    A2b[Language Rules]
    A2c[Development Guideline]
    A2 --> A2a
    A2 --> A2b
    A2 --> A2c

    A2a1[react-native-expo.mdc]
    A2a --> A2a1

    A2b1[typescript.mdc]
    A2b2[markdown.mdc]
    A2b --> A2b1
    A2b --> A2b2

    A2c1[testing.mdc]
    A2c2[security.mdc]
    A2c --> A2c1
    A2c --> A2c2
```

## Features

- Collect Cursor rule files from different projects
- Classify and organize rule files
- Provide standardized rule templates
- Facilitate sharing and reuse of rules across projects

## Usage

1. Browse the rules for the relevant language and framework
2. Apply the applicable rules to your project
3. Contribute your own rules back
