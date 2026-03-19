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
- When a boundary is repeatedly crossed incorrectly, document or enforce the rule instead of relying on memory.

## Change Hygiene
- Update names, imports, and related references together.
- Avoid silent behavior changes.
- Leave the touched area easier to read than before.
- Prefer changes that are easy to review, revert, and verify.
