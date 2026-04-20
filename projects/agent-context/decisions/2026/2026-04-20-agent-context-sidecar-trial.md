---
date: 2026-04-20
recorded_at: 2026-04-20T12:57:59.701Z
project: agent-context
topic: agent-context-sidecar-trial
source: agent
status: active
---
# Decision

## Context

The project is intended to reduce startup context cost for AI agents working on a large frontend codebase. The team already has an external task tracker, so planning and execution history do not need to be duplicated. Early adoption will likely be driven by one person and the documentation may live рядом with the main repository before any deep integration.

## Decision

Use a sidecar project called agent-context as a trial knowledge layer focused on bounded bootstrap context, task routing, constraints, decisions, and runbooks, while excluding tracker-owned backlog and session-history layers from the core model.

## Consequences

- The project can be introduced without changing the main product repository structure immediately.
- The first value should come from a small entry layer and task-routing artifacts rather than a full memory system.
- Knowledge should remain in ordinary files and canonical memory records first; MCP or richer automation can be added later if the structure proves useful.
- The documentation must state its maturity and authority explicitly during the trial period.

## Stable Guidance Review

- Outcome: updated
- Summary: Reviewed current stable guidance and updated the stable guidance in the same change slice.
