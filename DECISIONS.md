# Decisions

## What this file is
Every architectural and product decision made on CXS, in order.
Date every entry. Never delete. Add a reason for every decision.

---

## [2026-03-15] Build CXS as the first component of Restacked.ai

Decision: Start with the Context Manager (CXS) before MCP endpoints or gateway.
Reason: CXS is the foundation everything else builds on. Without a way to create
and manage context files, nothing else in the stack works. It is also the fastest
to prototype and validate with real users.

## [2026-03-15] Use GitHub as the context store

Decision: All context files live in GitHub repos as plain markdown.
Reason: Version controlled, change-tracked, PR-reviewable, works with every
existing AI tool via GitMCP. No proprietary format or lock-in.

## [2026-03-15] Three repo tiers per project

Decision: Company tier, domain tier, project tier as separate repos.
Reason: Separation of concerns. Company context is reused across all projects.
Domain context compounds across projects in the same vertical.
Project context is specific to one build.

## [2026-03-15] PAT instead of GitHub OAuth for MVP

Decision: Users paste a GitHub Personal Access Token. No OAuth flow.
Reason: OAuth requires a backend callback handler. PAT lets us validate
the core editing experience without infrastructure overhead.
OAuth added post-MVP once core flow is validated.

## [2026-03-15] Supabase as the backend

Decision: Supabase for auth, user data, and saved repo configurations.
Reason: Fastest path to a working backend on Vercel. Supabase Auth handles
user accounts. No custom backend needed in MVP.

## [2026-03-15] Plain textarea editor in MVP

Decision: No rich markdown editor, no preview pane in MVP.
Reason: Core value is read/edit/commit to GitHub. Editor experience is
a polish problem. Validate the workflow first.

## [2026-03-15] Prototype in v0, production rewrite in Cursor

Decision: Leonardo prototypes CXS UI in v0. Egor rewrites into production.
Reason: Follows the prototype/production rule. v0 validates the UI flow.
Cursor with full context produces the clean production implementation.

## [2026-03-15] Commit directly to default branch in MVP

Decision: All saves commit directly to main. No branch management.
Reason: Unnecessary complexity before core flow is validated.
Branch support added post-MVP if users need it.
