# Open Questions

## What this file is
Unresolved decisions that are blocking or will block development.
Review at the start of every work session. Move to DECISIONS.md when resolved.

---

## [BLOCKING] How is the GitHub PAT stored?

Question: Do we store the PAT in Supabase encrypted, in localStorage only,
or give the user the choice?
Why it matters: Security and UX. Supabase storage means it persists across
devices. localStorage means it never leaves the browser but resets on clear.
Who resolves: Egor
Target: Before any Supabase schema is defined

## [BLOCKING] What is the Supabase schema for MVP?

Question: What tables do we need? Minimum: users, projects, repo configurations.
What else?
Why it matters: Egor cannot start the production rewrite without a stable schema.
Who resolves: Egor + Tim
Target: Before production rewrite begins

## [IMPORTANT] How does a user create a new project?

Question: Does a project map 1:1 to a set of three repos (company, domain, project)?
Can a user have multiple projects? Can repos be shared across projects?
Why it matters: Core data model decision. Affects schema and UI.
Who resolves: Tim (product), Egor (technical feasibility)
Target: Before MCP endpoint work begins

## [IMPORTANT] What happens when a file has merge conflicts?

Question: If two team members edit the same file, how does CXS handle it?
Do we show a conflict warning? Block the save? Last write wins?
Why it matters: Multi-user editing is a real use case from day one.
Who resolves: Egor
Target: Post-MVP but needs a documented decision before launch

## [IMPORTANT] Auto-generated files in project tier

Question: SCHEMA.md, TYPES.md, API.md, ROLES.md, CODEBASE-MAP.md are
auto-generated from the home base. Does CXS trigger this generation,
display it read-only, or both?
Why it matters: Affects the editor UI - some files should not be manually editable.
Who resolves: Tim + Egor
Target: Before Phase 2 of CXS build

## [LATER] MCP endpoint generation

Question: When does CXS automatically expose repos as MCP endpoints?
Is this a one-click action per project or automatic on repo connection?
Who resolves: Tim + Egor
Target: MCP layer planning session

## [LATER] Domain context library

Question: How are pre-built domain libraries (aviation, hospitality, etc.)
packaged and loaded into a new project? Are they forks, copies, or live references?
Who resolves: Tim
Target: Post-MVP
