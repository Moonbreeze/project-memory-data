---
date: 2026-03-14
project: project-memory
topic: work-item-dependency-model
source: user
status: active
---
# Decision

## Context

A single decision may generate multiple implementation tracks. Some of those tracks can proceed independently, while others must wait for earlier slices to finish. If dependency and ordering are left implicit in prose or chronology, backlog planning and agent read flows will not be able to distinguish ready work from blocked work.

## Decision

Model work-item relationships explicitly. Allow one decision to spawn multiple work items, support both parallel and sequential execution, and represent ordering constraints through explicit dependency links rather than through document dates, text-only conventions, or status alone.

## Consequences

- The future work-item schema should include an explicit way to reference the originating decision and zero or more dependent work items.
- Backlog and planning views will need to distinguish ready items from blocked items based on dependency state, not just on open versus in-progress labels.
- A single architectural decision can be implemented through several independent work branches without forcing them into one oversized work item.
- Sequential implementation chains can be represented without encoding workflow order in free-form narrative text.
