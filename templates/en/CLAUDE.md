# CLAUDE.md

## Working Agreement
- Read `AGENTS.md` and the relevant docs before editing code.
- For non-trivial work, produce a short written plan before implementation.
- Keep edits minimal, local, and consistent with existing patterns.
- Do not assume undocumented behavior; verify from code, tests, or docs.
- Do not claim completion without fresh verification evidence.

## Default Workflow
### 1. Understand
- Read `docs/index.md` first.
- Follow its links into standards, architecture, plans, decisions, and runbooks.
- If the task touches only one small area, keep exploration narrow.

### 2. Plan
Write a lightweight plan when the task is non-trivial, spans multiple files, changes behavior, or has architectural risk.

A good lightweight plan includes:
- goal
- constraints
- files involved
- implementation approach
- validation steps
- done condition

Create or update a durable plan under `docs/plans/active/` when work needs multi-step tracking, handoff safety, or more than one session to complete.

### 3. Implement
- Make the smallest worthwhile change.
- Follow documented layering and ownership boundaries.
- Prefer clarity over cleverness.
- Do not add speculative abstractions, compatibility shims, or extra configurability unless the task requires them.

### 4. Verify
Run the relevant verification before reporting success.

Typical checks:
- focused tests for the changed behavior
- broader regression checks for the touched area
- lint, typecheck, or build commands when relevant
- manual runbook checks for user-facing flows or operational procedures

### 5. Document
Update docs when behavior, rules, architecture, or operating procedures changed.

## Command Use
Use the repository command docs under `.claude/commands/` as the default operating contract:
- `plan.md` for planning expectations
- `implement.md` for implementation expectations
- `verify.md` for verification expectations
- `cleanup.md` for small post-change maintainability cleanup

## Quality Bar
Before finishing, make sure:
- the requested task is actually solved
- the change is minimal and understandable
- verification was run fresh
- docs and plans are updated when needed
- remaining risks or follow-ups are explicit

## Response Style
When reporting work:
- cite the files changed
- summarize what was verified
- state what could not be verified
- call out remaining risks or assumptions
- distinguish clearly between completed work and recommended follow-up
