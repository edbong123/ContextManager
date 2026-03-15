# Context Files — Restacked.ai / CXS

This folder contains the AI context foundation for the CXS project.
Every AI session working on CXS should load these files before generating
any code, making any decisions, or producing any output.

---

## How to use this folder

### In Claude Projects
Upload all files to the Project knowledge base.
They are loaded automatically on every session.

### In Cursor / Claude Code
Add the repo as an MCP endpoint via GitMCP.
All files are served automatically at session start.

### In v0 or Lovable
Paste the contents of the relevant files into the system prompt
or project instructions before starting a session.

---

## File index

### COMPANY.md
**What it contains:** Who Restacked.ai is, what we are building, the team,
the three personas we build for, and the core insight behind the product.

**Load when:** Starting any session. This is always loaded first.
Never skip this file.

**Key questions it answers:**
- What is Restacked.ai?
- Who is on the team and what does each person do?
- Who are we building for?

---

### TOOLCHAIN.md
**What it contains:** The full technology stack for CXS. Frontend, backend,
hosting, GitHub integration method, AI tooling, and explicit list of what
we are not using and why.

**Load when:** Any session involving code generation, architecture decisions,
or stack choices. Load second, after COMPANY.md.

**Key questions it answers:**
- What framework, database, and hosting do we use?
- How does GitHub integration work in MVP?
- What is explicitly out of scope for MVP?

---

### STANDARDS.md
**What it contains:** Coding conventions for CXS. TypeScript rules, file
and folder structure, naming conventions, component rules, data fetching
rules, error handling, and commit message format.

**Load when:** Any session generating code. Load third, after TOOLCHAIN.md.
Non-negotiable for any production rewrite session.

**Key questions it answers:**
- Where do GitHub API calls go?
- Where do Supabase calls go?
- How are files and components named?
- What patterns are explicitly forbidden?

---

### AI-WORKFLOW.md
**What it contains:** The prototype/production rule, who uses which AI tools,
context loading order, the full prototype cycle step by step, context
maintenance rules, and what the AI should always know about this project.

**Load when:** Any session involving team workflow, tool decisions, or
process questions. Also load when onboarding a new team member to the project.

**Key questions it answers:**
- What is the prototype/production rule?
- Who owns context maintenance?
- What does Leonardo vs Egor vs Tim each do?
- What can the AI never do in a frontend session?

---

### DECISIONS.md
**What it contains:** Every architectural and product decision made on CXS,
in chronological order. Each entry has a date, a decision, and a reason.
This file grows with every session.

**Load when:** Every session, every time. This file tells the AI what has
already been decided so it does not re-open closed questions or suggest
approaches that were already rejected.

**Key questions it answers:**
- Why are we using PAT instead of OAuth?
- Why is the editor a plain textarea?
- Why are we committing directly to main?
- What was decided and when?

---

### OPEN-QUESTIONS.md
**What it contains:** Unresolved decisions that are blocking or will block
development. Each entry has a priority (BLOCKING, IMPORTANT, LATER),
the question, why it matters, who resolves it, and a target timeline.

**Load when:** Every session. The AI should flag if a session is about to
make a decision that belongs in this file. When a question is resolved,
move it to DECISIONS.md.

**Key questions it answers:**
- What is not yet decided?
- What is blocking the next step?
- Who needs to resolve what before we can proceed?

---

## Load order

Always load in this order:

1. COMPANY.md
2. TOOLCHAIN.md
3. STANDARDS.md
4. AI-WORKFLOW.md
5. DECISIONS.md
6. OPEN-QUESTIONS.md

---

## Rules for AI sessions using this context

- Never suggest a technology not in TOOLCHAIN.md without flagging it explicitly
- Never re-open a question already resolved in DECISIONS.md
- Always check OPEN-QUESTIONS.md before making an assumption about
  anything unresolved
- If a session produces a new decision, flag it for addition to DECISIONS.md
- If a session surfaces a new unresolved question, flag it for OPEN-QUESTIONS.md
- Prototype code is never deployed. It is always rewritten by Egor in Cursor.
- Leonardo never makes backend or database architecture decisions.
  Flag and stop if a session requires one.

