# Toolchain

## Frontend
- Framework: Next.js (App Router)
- UI components: shadcn/ui
- Styling: Tailwind CSS
- Language: TypeScript

## Backend / Database
- Platform: Supabase
- Used for: user accounts, saved repo configurations, PAT storage (encrypted)
- Auth: Supabase Auth

## Hosting
- Platform: Vercel
- Deployment: auto-deploy on push to main

## GitHub Integration
- GitHub REST API (no OAuth in MVP)
- Auth method: Personal Access Token (classic, repo scope)
- Token stored: Supabase (encrypted) per user session

## AI Tooling
- Prototyping: v0 (UI generation)
- Development: Cursor (production rewrite)
- Context: Claude Projects (shared team context)

## Key constraints
- No custom backend in MVP - Supabase handles all persistence
- All GitHub operations client-side via REST API
- No branch management - all commits to default branch only
- No markdown preview in MVP - plain textarea editor only

## What we are NOT using (and why)
- OAuth for GitHub: too slow to prototype, PAT is sufficient for MVP
- Custom API routes in MVP: unnecessary complexity before validation
- A rich markdown editor: out of scope until core flow is validated
