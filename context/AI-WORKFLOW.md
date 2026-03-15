# AI Workflow

## Prototype / production rule
Prototype code is never deployed to production. It is rewritten.
The vibe coder's output is a validated specification.
The full stack dev rewrites it into production. This is not optional.

## Who uses which tools
- Leonardo (vibe coder): v0 for UI generation, Lovable for full flows
- Tim (PM): Claude Projects for context, decisions, and planning
- Egor (full stack dev): Cursor and Claude Code for production rewrite

## Context loading at session start
Every AI session loads context in this order:
1. COMPANY.md
2. TOOLCHAIN.md
3. STANDARDS.md
4. AI-WORKFLOW.md
5. DECISIONS.md (project tier)
6. OPEN-QUESTIONS.md (project tier)

Load via Claude Project (Level 1) or MCP endpoints when live (Level 2).

## Prototype cycle
1. Tim defines the feature scope in DECISIONS.md and OPEN-QUESTIONS.md
2. Leonardo prototypes in v0 or Lovable with context loaded
3. Tim reviews prototype for product accuracy
4. Egor reviews prototype for technical feasibility
5. Approved prototype becomes the specification for production rewrite
6. Egor rewrites into production in Cursor with full context loaded
7. Tim updates DECISIONS.md with anything resolved during the rewrite

## Context maintenance rules
- Every architectural decision goes into DECISIONS.md same day
- Every unresolved question goes into OPEN-QUESTIONS.md immediately
- DECISIONS.md and OPEN-QUESTIONS.md are reviewed at the start of every work session
- Knowledge produced in sessions that stays in Slack or chat never reaches the AI
  it must be translated into a context file

## Context Maintainer
Tim owns context maintenance for CXS.
It is never nobody's job.

## AI review rules
- No AI-generated code goes to production without Egor reviewing it
- Leonardo never makes backend or database architecture decisions
- If a prototype session requires a schema or API change, stop and
  flag to Egor before continuing

## What the AI should always know
- Stack: Next.js, Supabase, shadcn/ui, Tailwind, TypeScript
- GitHub integration via PAT only, no OAuth in MVP
- All GitHub API calls go through /lib/github.ts
- All Supabase calls go through /lib/supabase.ts
- No direct API calls inside components
- Prototype is never deployed - always rewritten
