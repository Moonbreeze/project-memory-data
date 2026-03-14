---
date: 2026-03-14
project: project-memory
topic: work-item-dependency-follow-up
source: agent
status: active
---
# Session Note

## Summary

Extended the future work-item model with explicit dependency semantics so one decision can generate parallel or sequential execution slices. The follow-up also refined planning reads to distinguish ready work from blocked work based on dependency state.

## Actions

- Recorded a decision that work-item ordering and dependency must be represented explicitly rather than inferred from prose, chronology, or lifecycle labels alone.
- Added a planning baseline runbook for future work-item dependency handling, including fan-out from a shared decision and explicit blocked versus ready interpretation.
- Added a read-side refinement runbook so future backlog entrypoints can prioritize executable slices instead of returning a flat open-item list.

## Follow-up

- Reflect dependency metadata in the future work-item schema proposal.
- Use dependency-aware planning states when designing backlog views and read entrypoints.
- Keep the originating decision as rationale context without overloading it as an execution-order container.
