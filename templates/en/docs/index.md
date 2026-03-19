# Documentation Index

Use this file as the main navigation point for repository guidance.

## Recommended Reading Order
1. `../AGENTS.md` at the repository root
2. `standards/README.md`
3. `architecture/README.md` when system structure or ownership matters
4. `plans/active/README.md` for in-flight work
5. `runbooks/verification.md` before final verification

## How to Use This Docs Tree
- Start with standards when deciding how to work.
- Read architecture docs before changing boundaries, dependencies, or ownership.
- Use plans for non-trivial work that needs durable execution context.
- Use decisions for stable engineering or architecture choices that should not live only in plans.
- Use runbooks for local development, debugging, observability, and verification procedures.

## Sections
### Standards
- `standards/` — stable rules for coding, testing, logging, review, and repository behavior
- Start at `standards/README.md`

### Architecture
- `architecture/` — system shape, dependency direction, and domain boundaries
- Start at `architecture/README.md`

### Plans
- `plans/active/` — in-flight execution plans
- `plans/completed/` — completed work kept for history and traceability
- `plans/tech-debt/` — important debt that is visible but not yet scheduled

### Decisions
- `decisions/README.md` — concise ADR-style records for durable technical decisions

### Runbooks
- `runbooks/local-dev.md` — local setup and daily development workflow
- `runbooks/debugging.md` — fastest safe paths for issue investigation
- `runbooks/observability.md` — logs, metrics, traces, and production signal usage
- `runbooks/verification.md` — required validation before completion

## When to Update Docs
Update this tree when:
- repository rules changed
- architecture or ownership boundaries changed
- verification workflows changed
- a repeated prompting pattern should become documented guidance
- a stable decision should no longer live only in a plan or review thread

## Extension Guidance
- Keep docs short, explicit, and easy for agents to follow.
- Prefer operational guidance over narrative background.
- Put stable rules in `standards/`.
- Put task-specific execution detail in `plans/`.
- Put durable trade-offs and chosen directions in `decisions/`.
- Put repeatable procedures in `runbooks/`.
- Link new project-level guidance from here so it stays discoverable.
