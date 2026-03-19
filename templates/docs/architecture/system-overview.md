# System Overview

Describe the system in terms of major components and how they interact.

## Suggested Sections
- entry points
- core domains or services
- data stores and external dependencies
- major request or event flows
- important background jobs, queues, or scheduled work
- main operational signals such as logs, metrics, and traces

## Questions This Doc Should Answer
- What are the main parts of the system?
- Where does business logic belong?
- Which dependencies are external versus internal?
- What parts are safe to change together?
- Which flows are most important to verify after a change?

## Writing Guidance
- Start with the stable shape of the system, not low-level implementation detail.
- Prefer a short diagram, table, or bullets over dense prose.
- Link out to domain, layering, and decision docs when they hold deeper detail.

## Maintenance Rule
Update this file when the system shape or major responsibilities change.
