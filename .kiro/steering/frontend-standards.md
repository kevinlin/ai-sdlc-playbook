---
inclusion: fileMatch
fileMatchPattern: '*.tsx|*.jsx|*.vue|*.svelte'
---

# Frontend Development Standards

## Component Architecture
- Use functional components with hooks (React)
- Keep components small and focused
- Implement proper prop validation
- Use TypeScript for type safety
- Follow component composition patterns

## State Management
- Use local state for component-specific data
- Implement global state for shared application data
- Use proper state management libraries (Redux, Zustand, Pinia)
- Avoid prop drilling with context or state management

## Styling Guidelines
- Use CSS modules or styled-components for component styling
- Follow BEM methodology for CSS class naming
- Implement responsive design with mobile-first approach
- Use CSS custom properties for theming
- Maintain consistent spacing and typography scales

## Performance Optimization
- Implement code splitting and lazy loading
- Use React.memo or similar for expensive components
- Optimize images and assets
- Implement proper caching strategies
- Monitor bundle size and performance metrics

## Accessibility Standards
- Use semantic HTML elements
- Implement proper ARIA attributes
- Ensure keyboard navigation support
- Maintain proper color contrast ratios
- Test with screen readers

## Testing Strategy
- Write unit tests for utility functions
- Use React Testing Library for component tests
- Implement visual regression testing
- Test user interactions and workflows
- Mock external dependencies properly