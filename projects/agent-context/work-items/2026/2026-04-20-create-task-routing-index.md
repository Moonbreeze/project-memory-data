---
date: 2026-04-20
recorded_at: 2026-04-20T13:21:19.130Z
project: agent-context
topic: create-task-routing-index
source: agent
status: active
work_item_state: open
---
# Work Item

## Summary

Define the routing entry model the harness uses to choose the next bounded project-memory read for a concrete task.

## Outcome

A reusable routing pattern exists for modules, skills, and project-memory-backed task startup instead of relying on repo-local ENTRYPOINTS files.

## Provenance

- ad-hoc: Initial implementation planning for the agent-context MVP, now reframed around the authoring-repo and project-memory split.

## Dependencies

- work-item:agent-context:2026-04-20:scaffold-agent-context-structure
- work-item:agent-context:2026-04-20:write-start-bootstrap-flow

## Context

- canonical-doc:agent-context:2026-06-21:task-routing
- canonical-doc:agent-context:2026-06-21:documentation-model
- decision:agent-context:2026-06-21:authoring-repo-project-memory-split

## Verification

- Define a routing format that includes task type or intent, where to start, what to inspect next, pitfalls, and how to verify.
- The routing model can be consumed by behavior artifacts such as modules or skills rather than only by one repository-local Markdown index.
- Entries point to bounded memory reads, repository paths, or explicit placeholders when the route is not yet concrete.

## Evidence

- none
