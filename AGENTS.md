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

ALWAYS use context7 to gather up to date documentation for the libraries you're going to implement.
NEVER invent documentation, especially when you run into a difficult bug to solve

# Package manager

ALWAYS use the package manager already used in the code base.
For new projects, DEFAULT to pnpm.

# Task List Management

Guidelines for creating and managing task lists in Markdown files to track project progress

## Task List Creation

1. Create task lists in a markdown file (in the project root):
   - Use `TASKS.md` or a descriptive name relevant to the feature (e.g., `ASSISTANT_CHAT.md`)
   - Include a clear title and description of the feature being implemented

2. Structure the file with these sections:

   ```markdown
   # Feature Name Implementation

   Brief description of the feature and its purpose.

   ## Completed Tasks

   - [x] Task 1 that has been completed
   - [x] Task 2 that has been completed

   ## In Progress Tasks

   - [ ] Task 3 currently being worked on
   - [ ] Task 4 to be completed soon

   ## Future Tasks

   - [ ] Task 5 planned for future implementation
   - [ ] Task 6 planned for future implementation

   ## Implementation Plan

   Detailed description of how the feature will be implemented.

   ### Relevant Files

   - path/to/file1.ts - Description of purpose
   - path/to/file2.ts - Description of purpose
   ```

## Task List Maintenance

1. Update the task list as you progress:
   - Mark tasks as completed by changing `[ ]` to `[x]`
   - Add new tasks as they are identified
   - Move tasks between sections as appropriate

2. Keep "Relevant Files" section updated with:
   - File paths that have been created or modified
   - Brief descriptions of each file's purpose
   - Status indicators (e.g., ✅) for completed components

3. Add implementation details:
   - Architecture decisions
   - Data flow descriptions
   - Technical components needed
   - Environment configuration

## Instructions

When working with task lists, you should:

1. Regularly update the task list file after implementing significant components
2. Mark completed tasks with [x] when finished
3. Add new tasks discovered during implementation
4. Maintain the "Relevant Files" section with accurate file paths and descriptions
5. Document implementation details, especially for complex features
6. When implementing tasks one by one, first check which task to implement next
7. After implementing a task, update the file to reflect progress

## Example Task Update

When updating a task from "In Progress" to "Completed":

```markdown
## In Progress Tasks

- [ ] Implement database schema
- [ ] Create API endpoints for data access

## Completed Tasks

- [x] Set up project structure
- [x] Configure environment variables
```

Should become:

```markdown
## In Progress Tasks

- [ ] Create API endpoints for data access

## Completed Tasks

- [x] Set up project structure
- [x] Configure environment variables
- [x] Implement database schema
```
