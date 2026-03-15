# Standards

## Language
- TypeScript everywhere, no exceptions
- Strict mode enabled
- No `any` types

## File and folder structure
- Next.js App Router conventions
- Feature-based folders under /app and /components
- Shared UI components in /components/ui (shadcn)
- Custom components in /components
- Utility functions in /lib
- Supabase client in /lib/supabase.ts
- GitHub API calls in /lib/github.ts

## Naming conventions
- Components: PascalCase (FileTree.tsx, EditorPanel.tsx)
- Functions and variables: camelCase
- Constants: UPPER_SNAKE_CASE
- Files: kebab-case except components
- Database tables: snake_case

## Components
- shadcn/ui as the base for all UI primitives
- No inline styles - Tailwind classes only
- No custom CSS files unless absolutely unavoidable
- Every component typed with explicit props interface

## Data fetching
- All GitHub API calls go through /lib/github.ts only
- No direct fetch() calls to GitHub API inside components
- All Supabase calls go through /lib/supabase.ts only

## State management
- React useState and useContext only in MVP
- No external state library until complexity justifies it

## Error handling
- All GitHub API calls wrapped in try/catch
- User-facing errors shown via shadcn toast
- No silent failures

## Commits
- Commit messages: present tense, one line, plain English
- Example: "add file tree sidebar" not "added sidebar component"

## What we do not do
- No class components
- No CSS modules
- No barrel exports (index.ts re-exports)
- No direct Supabase calls inside components
