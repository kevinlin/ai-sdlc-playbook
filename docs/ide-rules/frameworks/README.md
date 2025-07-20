# Framework IDE Rules

This directory contains IDE rules specific to different software frameworks and libraries. These rules are compatible with multiple AI-powered IDEs including Cursor, Kiro, and other similar development environments.

## Backend Frameworks

- **[Django](./django.md)**: Django project structure, model design, and best practices
- **[Express.js](./node-express.md)**: Express.js application structure and conventions
- **[FastAPI](./fastapi.md)**: FastAPI project organization and best practices
- **[Flask](./flask.md)**: Flask application structure and development standards
- **[NestJS](./typescript-nestjs.md)**: NestJS architecture and development standards
- **[Spring Boot Core](./spring-boot-core.md)**: Spring Boot core concepts and best practices
- **[Spring Boot REST](./spring-boot-rest.md)**: Spring Boot REST API development standards
- **[Spring Data JDBC](./spring-data-jdbc.md)**: Spring Data JDBC configuration and best practices

## Testing Backend Frameworks

- **[Spring Boot Integration Testing](./spring-boot-integration-testing.md)**: Spring Boot integration testing strategies and best practices
- **[Spring Boot Local Testing](./spring-boot-local-testing.md)**: Spring Boot local testing setup and guidelines
- **[Spring Boot Slice Testing](./spring-boot-slice-testing.md)**: Spring Boot slice testing techniques and practices

## Frontend Frameworks

- **[Next.js](./nextjs.md)**: Next.js project structure and best practices
- **[React](./react.md)**: React component structure, hooks usage, and best practices
- **[Svelte](./svelte.md)**: Svelte component architecture and best practices
- **[Tailwind CSS](./tailwind.md)**: Tailwind CSS styling guidelines and conventions
- **[Vue.js](./vuejs.md)**: Vue component architecture, state management, and conventions

## Mobile Development Frameworks

- **[Flutter](./flutter.md)**: Flutter widget structure and Dart best practices
- **[React Native](./react-native.md)**: React Native component structure and best practices
- **[React Native with Expo](./react-native-expo.md)**: Expo-specific guidelines for React Native
- **[SwiftUI](./swiftui.md)**: SwiftUI view structure and Swift best practices

## Usage

### For Cursor IDE
1. Identify the framework(s) used in your project
2. Copy the relevant MDC rule content to your project's `.cursor/rules` directory
3. Customize as needed to align with your project's specific requirements

### For Kiro IDE
1. Identify the framework(s) used in your project
2. Copy the relevant Markdown content to your project's `.kiro/steering` directory
3. Modify the front-matter inclusion settings as needed

### For Other IDEs
1. Adapt the rule content format to your IDE's requirements
2. Use the core framework guidelines while adjusting the metadata format

## Contributing

If you'd like to contribute improvements to existing framework rules or add support for additional frameworks, please submit a pull request. Ensure your contributions include support for both Cursor and Kiro formats. 