---
date: 2026-03-14
project: project-memory
topic: scenario-and-graph-first-design
source: user
status: active
---
# Decision

## Context

The project is preparing a larger documentation-model change around canonical project docs and future work-item support. Jumping directly to tool surfaces, agent skills, or rules would risk encoding an unclear domain model and repeating the current mismatch between backlog behavior and document lifecycle.

## Decision

Start the next implementation phase with explicit user scenarios and document-state graphs. Derive canonical docs, agent skills, and project-specific agent rules from those scenario flows and lifecycle models instead of designing them independently first.

## Consequences

- The first follow-up sessions should produce a compact set of core scenarios plus lifecycle and transition diagrams for the relevant document types.
- Canonical-doc implementation can be scoped against concrete workflows rather than abstract capability lists.
- Agent skills and rules can be kept short and behaviorally precise because they will reflect a reviewed workflow model.
- Implementation can be split into multiple sessions with a shared reference document set instead of relying on conversational context.
