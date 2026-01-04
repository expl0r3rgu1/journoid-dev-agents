# Next.js

# Next.js rules

- Use the App Router structure with `page.tsx` files in route directories.
- Client components must be explicitly marked with `'use client'` at the top of the file.
- Use kebab-case for directory names (e.g., `components/auth-form`) and component files.
- Prefer default exports over named exports, i.e. `export default function Button() { /* ... */ }` instead of `export function Button() { /* ... */ }`.
- Minimize `'use client'` directives:
  - Keep most components as React Server Components (RSC)
  - Only use client components when you need interactivity and wrap in `Suspense` with fallback UI
  - Create small client component wrappers around interactive elements
- Avoid unnecessary `useState` and `useEffect` when possible:
  - Use server components for data fetching
  - Use React Server Actions for form handling
  - Use URL search params for shareable state
- Use `nuqs` for URL search param state management

# Tailwind CSS

# Tailwind CSS rules

- Use responsive prefixes for mobile-first design:

```html
<div class="w-full md:w-1/2 lg:w-1/3"></div>
```

- Use state variants for interactive elements:

```html
<button class="bg-blue-500 hover:bg-blue-600 focus:ring-2">Click me</button>
```

- Use arbitrary values for specific requirements:

```html
<div class="top-[117px] grid-cols-[1fr_2fr]"></div>
```

- Prefer the use of flex, gap, grid as utilities for consistent layout:

```html
<div class="flex flex-col gap-2">
  <div>Item 1</div>
  <div>Item 2</div>
</div>
```

- Don't use margins `m`, prefer padding `p`:

```html
<button class="border border-muted p-4">Click me</button>
```

# Documentation
When you need to search docs, ALWAYS use `context7` tools.
NEVER invent documentation, especially when you run into a difficult bug to solve.

# Package manager

ALWAYS use the package manager already used in the code base.
For new projects, DEFAULT to pnpm.
