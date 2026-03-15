---
date: 2026-03-15
project: project-memory
topic: work-item-context-work-item-locators
source: agent
status: draft
---
# Decision

## Context

The current work-item model already supports explicit work-item relationships through dependencies and separates them from contextual references to decisions, canonical docs, and session notes. One possible future refinement would allow a work-item locator inside the work-item context section to represent a related but non-blocking work slice. However, that idea risks blurring the line between execution prerequisites and general contextual association. At the moment there is no pressure-tested use case that clearly requires a second work-item relation type beyond dependencies, and the existing planning/read model benefits from keeping that distinction sharp.

## Decision

Do not extend work-item context locators to include work-item references at this stage. Treat the idea as a possible future refinement only if a real use case emerges that cannot be modeled cleanly through dependencies, topic-based planning reads, or ordinary explanatory documents. Until then, keep work-item-to-work-item execution relations in dependencies only and preserve context for non-work-item governing or explanatory records.

## Consequences

- The current work-item model stays semantically narrow: dependencies remain the only built-in work-item-to-work-item relation type.
- Planning and bounded-read behavior avoid a second ambiguous work-item relation that could weaken the blocked-versus-related distinction.
- If a future use case appears, the project can revisit the idea with explicit semantics, guardrails, and read behavior instead of inheriting an underspecified context relation.
- The absence of work-item locators in context is now an intentional model boundary rather than an accidental omission.
