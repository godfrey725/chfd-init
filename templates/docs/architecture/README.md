# Architecture

This directory explains how the system is structured so changes can respect existing boundaries.

## Read These When
- a task crosses module or service boundaries
- you are adding a new subsystem or major dependency
- you are unsure where code should live

## Files
- `system-overview.md` — high-level system shape
- `layering-rules.md` — dependency direction and boundary rules
- `domain-map.md` — domain concepts and ownership map

## Guidance
- Keep architecture docs short, explicit, and updated when boundaries change.
- Prefer diagrams or bullets that help agents decide where code belongs.
