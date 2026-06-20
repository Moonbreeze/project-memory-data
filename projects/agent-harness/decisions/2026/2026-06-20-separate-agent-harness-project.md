---
date: 2026-06-20
recorded_at: 2026-06-20T15:09:16.972Z
project: agent-harness
topic: separate-agent-harness-project
source: agent
status: active
---
# Decision

## Context

The proposed harness has its own architecture, routing logic, role definitions, execution lifecycle, and reusable operating guidance. Keeping these concerns inside one application project would mix product work with meta-level agent workflow design.

## Decision

Create a dedicated meta-project named agent-harness with its own project-memory surface and its own implementation backlog.

## Consequences

- Agent-harness gets an isolated backlog for its own evolution.
- Durable decisions about the harness no longer need to be embedded in unrelated product projects.
- The harness can be reused and refined across multiple repositories and workflows.
- Runtime artifacts and canonical guidance can evolve independently from any one application codebase.

## Stable Guidance Review

- Outcome: updated
- Summary: Reviewed current stable guidance and updated the stable guidance in the same change slice.
- Note: Initial architecture guidance is being established in canonical docs during bootstrap.
