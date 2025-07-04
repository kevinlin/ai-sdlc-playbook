# TypeScript, React Native, Expo, and Mobile UI Development Rules

To create a new Cursor Rule:

1. Enter the name as `react-native`
2. Copy & paste the file content from below

For more information, visit the [Project rules](https://docs.cursor.com/context/rules#project-rules).


```markdown
---
description: TypeScript, React Native, Expo, and Mobile UI Development Rules
globs: **/*.jsx, **/*.tsx
alwaysApply: false
---


# TypeScript, React Native, Expo, and Mobile UI Development Rules

## Code Style and Structure
- Write clear, readable code: Ensure your code is easy to read and understand. Use descriptive names for variables and functions.
- Use function components: Prefer function components with hooks (useState, useEffect, etc.) over class components.
- Component modularity: Break components down into smaller, reusable parts. Keep components focused on a single responsibility.
- Organize files by feature: Group related components, hooks, and styles by feature (e.g., user-profile).

## Naming Conventions
- Variables and functions: Use camelCase and descriptive names (e.g., isFetchingData, handleUserInput).
- Components: Use PascalCase for component names (e.g., UserProfile).
- Directories: Use lowercase and hyphens for directory names (e.g., user-profile).

## TypeScript Usage
- All code should use TypeScript; prefer interfaces over types
- Avoid enums; use maps instead
- Use function components with TypeScript interfaces
- Use strict mode in TypeScript for better type safety

## Syntax and Formatting
- Use the "function" keyword to define pure functions
- Avoid unnecessary braces in conditionals; use concise syntax for simple statements
- Use declarative JSX
- Use Prettier to maintain consistent code formatting

## UI and Styling
- Use Expo built-in components for common UI patterns and layouts
- Use Flexbox and Expo's useWindowDimensions for responsive design
- Use styled-components or Tailwind CSS for component styling
- Use Expo's useColorScheme for dark mode support
- Ensure high accessibility (a11y) standards, using ARIA roles and native accessibility props
- Use react-native-reanimated and react-native-gesture-handler for high-performance animations and gestures

## Safe Area Management
- Use SafeAreaProvider from react-native-safe-area-context to manage safe areas globally
- Wrap top-level components with SafeAreaView to handle notches, status bars, and other screen insets on iOS and Android
- Use SafeAreaScrollView for scrollable content, ensuring it respects safe area boundaries
- Avoid hardcoding padding or margin for safe areas; rely on SafeAreaView and context hooks

## Performance Optimization
- Minimize useState and useEffect; prefer context and reducers for state management
- Use Expo's AppLoading and SplashScreen to optimize app startup experience
- Optimize images: use WebP format where supported, include size data, and use expo-image for lazy loading
- Use React's Suspense and dynamic imports for code splitting and lazy loading of non-critical components
- Use React Native built-in tools and Expo debugging features to monitor performance
- Use component memoization, useMemo, and useCallback hooks to avoid unnecessary re-renders

## Navigation
- Use react-navigation for routing and navigation; follow best practices for stack, tab, and drawer navigators
- Leverage deep linking and universal links to enhance user engagement and navigation flow
- Use expo-router for dynamic routing for better navigation handling

## State Management
- Use React Context and useReducer for global state management
- Use react-query for data fetching and caching; avoid excessive API calls
- For complex state management, consider Zustand or Redux Toolkit
- Use libraries like expo-linking to handle URL search parameters

## Error Handling and Validation
- Use Zod for runtime validation and error handling
- Use Sentry or similar services for proper error logging
- Prioritize handling errors and edge cases:
  - Handle errors at the start of functions
  - Use early returns for error conditions to avoid deeply nested if statements
  - Avoid unnecessary else statements; use if-return pattern
  - Implement global error boundaries to catch and handle unexpected errors
- Use expo-error-reporter to log and report errors in production

## Testing
- Use Jest and React Native Testing Library for unit testing
- Use Detox for integration testing of critical user flows
- Use Expo's testing tools to run tests in different environments
- Consider snapshot testing for components to ensure UI consistency

## Security
- Sanitize user input to prevent XSS attacks
- Use react-native-encrypted-storage to securely store sensitive data
- Ensure secure communication with APIs using HTTPS and proper authentication
- Follow Expo's security guidelines to protect your app: https://docs.expo.dev/guides/security/

## Internationalization (i18n)
- Use react-native-i18n or expo-localization for internationalization and localization
- Support multiple languages and RTL layouts
- Ensure text scaling and font adjustment for better accessibility

## Key Conventions
1. Rely on Expo's managed workflow to simplify development and deployment
2. Prioritize mobile web performance metrics (load time, jank, and responsiveness)
3. Use expo-constants to manage environment variables and configuration
4. Use expo-permissions to gracefully handle device permissions
5. Implement expo-updates for over-the-air (OTA) updates
6. Follow Expo's best practices for app deployment and release: https://docs.expo.dev/distribution/introduction/
7. Ensure compatibility by extensively testing on both iOS and Android platforms

## API Documentation
- Use the official Expo documentation to set up and configure your project: https://docs.expo.dev/

Refer to the Expo documentation for best practices on Views, Blueprints, and Extensions.
```