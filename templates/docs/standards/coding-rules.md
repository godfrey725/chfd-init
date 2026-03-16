# Coding Rules

## General
- Match the repository's established style and structure.
- Make focused changes instead of unrelated cleanup.
- Prefer straightforward code over premature abstraction.
- Remove dead code when you are certain it is unused.

## Boundaries
- Keep responsibilities clear at file and module boundaries.
- Avoid introducing cross-layer dependencies without documenting them.
- Reuse existing project primitives before creating new helpers.

## Change Hygiene
- Update names, imports, and related references together.
- Avoid silent behavior changes.
- Leave the touched area easier to read than before.
