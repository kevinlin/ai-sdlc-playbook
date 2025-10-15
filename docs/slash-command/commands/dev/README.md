# Development Commands

This namespace contains commands for daily development tasks, code analysis, and productivity enhancements. These commands help streamline your development workflow.

## Available Commands

- **all-tools.md** - Access comprehensive development tools and utilities in one place
- **clean-branches.md** - Clean up local and remote Git branches that are no longer needed
- **code-review.md** - Perform comprehensive code reviews analyzing quality and best practices
- **code-to-task.md** - Convert code changes or features into actionable tasks
- **create-react-component.md** - Generate a new React component with tests and stories
- **debug-error.md** - Debug errors with detailed analysis and solution suggestions
- **directory-deep-dive.md** - Perform deep analysis of directory structures and contents
- **explain-code.md** - Get detailed explanations of complex code sections
- **fix-issue.md** - Automatically fix identified issues in your codebase
- **generate-tests.md** - Create comprehensive unit tests for current file or selected code
- **git-status.md** - Enhanced Git status with additional insights and recommendations
- **prime.md** - Prime your development environment for optimal performance
- **refactor-code.md** - Refactor code following best practices and design patterns
- **rule2hook.md** - Convert natural language project rules into Claude Code hooks automatically (by [zxdxjtu](https://github.com/zxdxjtu/claudecode-rule2hook))
- **sentient.md** - Advanced AI-powered development assistant with contextual awareness
- **ultra-think.md** - Deep thinking mode for complex problem solving and architecture decisions

---

## Create React Component

**Command**: `/dev:create-component [component-name] [styling-framework]`

Generate a new React component with TypeScript, tests, and Storybook stories.

### Usage

```bash
/dev:create-component Button styled-components
/dev:create-component UserCard tailwind
```

### What It Creates

The command generates a complete component structure:

- `src/components/[component-name]/[component-name].tsx` - Main component with TypeScript
- `src/components/[component-name]/[component-name].test.tsx` - Unit tests with React Testing Library
- `src/components/[component-name]/[component-name].stories.tsx` - Storybook stories
- `src/components/[component-name]/index.ts` - Barrel export

### Component Template

```typescript
interface ComponentNameProps {
  // Props will be added based on requirements
}

export const ComponentName: React.FC<ComponentNameProps> = (props) => {
  return (
    // Component implementation
  );
};
```

### Testing Requirements

- Test rendering with default props
- Test all interactive behaviors
- Test accessibility (ARIA labels, keyboard navigation)
- Achieve >80% code coverage

### Requirements

- Component name: First argument (required)
- Styling framework: Second argument (required)
- Includes TypeScript types and PropTypes
- Follows project's file structure conventions

---

## Generate Unit Tests

**Command**: `/dev:generate-tests`

Create comprehensive unit tests for the current file or selected code.

### Usage

```bash
/dev:generate-tests
```

Use this command when you have a file open or code selected, and it will generate appropriate unit tests.

### What It Generates

A complete test file with:

- Proper imports and setup
- beforeEach/afterEach hooks if needed
- Well-organized test suites using describe blocks
- Clear assertions
- Helpful comments for complex scenarios

### Test Coverage Goals

- Aim for >80% code coverage
- Test all public methods/functions
- Test error handling and edge cases
- Test with various input types
- Test async operations properly

### Testing Best Practices

The generated tests will:

- Use the project's testing framework (Jest, Vitest, etc.)
- Follow project's testing patterns and conventions
- Include positive test cases (happy path)
- Include negative test cases (error conditions)
- Test edge cases and boundary conditions
- Mock external dependencies appropriately
- Use descriptive test names that explain what is being tested