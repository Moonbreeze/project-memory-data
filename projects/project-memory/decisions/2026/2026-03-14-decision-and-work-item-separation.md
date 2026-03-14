---
date: 2026-03-14
project: project-memory
topic: decision-and-work-item-separation
source: user
status: active
---
# Decision

## Context

The current backlog view is implemented as active decisions, which mixes two different concepts: a decision that remains valid after implementation and a unit of work that should move through an execution lifecycle. The next major change, canonical project-doc support, makes that mismatch more costly because the system will need to distinguish stable architectural intent from current documentation and from outstanding implementation work.

## Decision

Keep active decisions as records of currently valid project decisions, not as backlog items. Model executable project work separately through a first-class work-item document type and do not change a decision lifecycle merely to indicate that implementation is complete.

## Consequences

- Backlog should move away from the current active-decision shortcut and eventually be driven by work-item documents instead.
- Decision lifecycle remains semantic: superseded means replaced by a newer decision, and archived means removed from the active body of documents rather than simply implemented.
- Canonical project docs can become the source of truth for current system behavior without forcing decision documents to carry task-tracking semantics.
- The project will need a dedicated work-item lifecycle and relations between work items, decisions, canonical docs, session notes, and verification results.
