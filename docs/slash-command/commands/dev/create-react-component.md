---
argument-hint: [component-name] [styling-framework]
description: Generate a new React component with tests and stories
---

# Create Component

Create a new React component named $1 using $2 for styling.

## Requirements

- Component name: $1
- Styling framework: $2
- Include TypeScript types
- Include PropTypes for runtime validation
- Create basic unit tests with React Testing Library
- Create Storybook stories with common use cases
- Follow project's file structure conventions

## File Structure

Generate the following files:
- `src/components/$1/$1.tsx` - Main component
- `src/components/$1/$1.test.tsx` - Unit tests
- `src/components/$1/$1.stories.tsx` - Storybook stories
- `src/components/$1/index.ts` - Barrel export

## Component Template

```typescript
interface ${1}Props {
  // Add props here
}

export const $1: React.FC<${1}Props> = (props) => {
  return (
    // Component implementation
  );
};
```

## Testing Requirements

- Test rendering with default props
- Test all interactive behaviors
- Test accessibility (ARIA labels, keyboard navigation)
- Achieve >80% code coverage
