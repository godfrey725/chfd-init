# Layering Rules

Define allowed dependency directions for the repository.

## Core Principle
Dependencies should flow inward toward stable domain logic, not outward toward incidental details.

## Rules
- UI, handlers, or delivery layers may depend on application and domain layers.
- Application orchestration may depend on domain logic and abstract interfaces.
- Infrastructure implementations may depend on domain abstractions but should not own business policy.
- Lower-level utilities should not import higher-level product code.

## Enforcement Ideas
- Add review checks for dependency direction when touching boundaries.
- Use lint rules, import guards, or test coverage where the stack supports them.
- Document intentional exceptions so they stay visible and reviewable.

## Review Questions
- Did this change introduce a dependency in the wrong direction?
- Is business logic leaking into delivery or infrastructure code?
- Should a new interface or boundary be documented here?
