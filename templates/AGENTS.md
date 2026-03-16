# AGENTS.md

This repository is configured for agent-assisted development.

## Mission
Build and change the system through small, verifiable steps. Read the repository guidance first, plan before non-trivial work, and keep implementation aligned with documented architecture and standards.

## Start Here
Before making changes, read these in order:

1. `docs/index.md`
2. `docs/standards/README.md`
3. `docs/architecture/README.md` if structure or ownership matters
4. `docs/plans/active/` for any in-flight work related to the task
5. the specific standards, architecture notes, and runbooks referenced by those docs

## Operating Loop
1. Understand the task and read the relevant docs.
2. For non-trivial work, write a short plan before implementation.
3. Make the smallest change that solves the task.
4. Verify the changed behavior with the relevant checks.
5. Update docs when repository rules, architecture, or workflows changed.

## Planning Expectations
Create a plan when work is non-trivial, crosses multiple files, changes behavior, or has more than one reasonable implementation path.

A good plan should capture:
- goal
- constraints
- files likely involved
- risks
- validation steps
- done condition

Store active plans under `docs/plans/active/` when the work needs durable tracking.

## Implementation Expectations
- Treat docs as the source of truth for repository conventions.
- Prefer small, reviewable changes over broad rewrites.
- Follow existing patterns unless the docs explicitly change them.
- Keep module boundaries explicit; do not couple unrelated layers just to make a change faster.
- Prefer deletion over compatibility layers that no longer serve the system.

## Verification Expectations
Do not call work complete without fresh verification evidence.

When relevant, verify with:
- targeted tests for the changed behavior
- broader regression tests for the touched area
- lint or type checks when the stack uses them
- runbook-based manual checks for workflows that are hard to test automatically

## Documentation Expectations
Update documentation when:
- repository rules changed
- architecture or ownership boundaries changed
- workflow or verification steps changed
- a plan is needed for non-trivial work

## Definition of Done
Work is done only when all of the following are true:
- the requested change is implemented
- relevant verification has been run and checked
- impacted docs are updated
- known risks or follow-ups are called out clearly
