---
description: Next.js development best practices covering SSR, routing, performance optimization, and modern React patterns.
---

# Next.js Best Practices

## IDE Configuration Headers

### For Cursor IDE

To create a new Cursor Rule:

1. Enter the name as `nextjs`
2. Copy & paste the following header and rule content below:

```markdown
---
description: Next.js Best Practices
globs: **/*.jsx, **/*.tsx, pages/**/*
alwaysApply: false
---
```

### For Kiro IDE

To create a new Kiro Steering Document:

1. Create a file named `nextjs.md` in `.kiro/steering/`
2. Copy & paste the following header and rule content below:

```markdown
---
inclusion: fileMatch
fileMatchPattern: '**/*.jsx,**/*.tsx,pages/**/*'
---
```

For more information about IDE rules, visit:
- [Cursor Project Rules](https://docs.cursor.com/context/rules#project-rules)
- [Kiro Steering Documents](https://github.com/kirolabs/kiro)

## Rule Content

```markdown
# Next.js Best Practices

## Project Structure
- Use the App Router directory structure
- Place components in `app` directory for route-specific components
- Place shared components in `components` directory
- Place utilities and helpers in `lib` directory
- Use lowercase with dashes for directories (e.g., `components/auth-wizard`)

## Components
- Use Server Components by default
- Mark client components explicitly with 'use client'
- Wrap client components in Suspense with fallback
- Use dynamic loading for non-critical components
- Implement proper error boundaries
- Place static content and interfaces at file end

## Performance
- Optimize images: Use WebP format, size data, lazy loading
- Minimize use of 'useEffect' and 'setState'
- Favor Server Components (RSC) where possible
- Use dynamic loading for non-critical components
- Implement proper caching strategies

## Data Fetching
- Use Server Components for data fetching when possible
- Implement proper error handling for data fetching
- Use appropriate caching strategies
- Handle loading and error states appropriately

## Routing
- Use the App Router conventions
- Implement proper loading and error states for routes
- Use dynamic routes appropriately
- Handle parallel routes when needed

## Forms and Validation
- Use Zod for form validation
- Implement proper server-side validation
- Handle form errors appropriately
- Show loading states during form submission

## State Management
- Minimize client-side state
- Use React Context sparingly
- Prefer server state when possible
- Implement proper loading states 
```