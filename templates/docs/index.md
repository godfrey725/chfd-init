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
- Use runbooks for local development, debugging, and verification procedures.

## Sections
- `standards/` — stable rules for coding, testing, logging, review, and repository behavior
- `architecture/` — system shape, dependency direction, and domain boundaries
- `plans/` — active plans, completed initiatives, and visible tech debt
- `runbooks/` — repeatable local-dev, debugging, and verification workflows

## When to Update Docs
Update this tree when:
- repository rules changed
- architecture or ownership boundaries changed
- verification workflows changed
- a repeated prompting pattern should become documented guidance

## Authoring Guidance
- Keep docs short, explicit, and easy for agents to follow.
- Prefer operational guidance over narrative background.
- Put stable rules in `standards/`.
- Put task-specific execution detail in `plans/`.
- Put repeatable procedures in `runbooks/`.
- Link new project-level guidance from here so it stays discoverable.
