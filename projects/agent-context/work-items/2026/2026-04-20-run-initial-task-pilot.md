---
date: 2026-04-20
recorded_at: 2026-04-20T13:22:12.873Z
project: agent-context
topic: run-initial-task-pilot
source: agent
status: active
work_item_state: open
---
# Work Item

## Summary

Run the project-memory-backed harness model on several real tasks to validate whether bounded startup reduces context cost.

## Outcome

The team has evidence about whether bounded project-memory reads plus shared harness behavior are enough for low-cost task startup.

## Provenance

- ad-hoc: Initial implementation planning for the agent-context MVP, now reframed around the authoring-repo and project-memory split.

## Dependencies

- work-item:agent-context:2026-04-20:write-start-bootstrap-flow
- work-item:agent-context:2026-04-20:create-task-routing-index
- work-item:agent-context:2026-04-20:seed-initial-recipes
- work-item:agent-context:2026-04-20:write-system-map
- work-item:agent-context:2026-04-20:define-context-curator-contract
- work-item:agent-context:2026-04-20:define-external-agent-context-entrypoint

## Context

- canonical-doc:agent-context:2026-06-21:agent-context-overview
- canonical-doc:agent-context:2026-06-21:task-routing
- canonical-doc:agent-context:2026-06-21:context-curator-model
- decision:agent-context:2026-06-21:authoring-repo-project-memory-split

## Verification

- Run three to five real task trials.
- For each task, determine whether cold-start context plus one planning or topic package and at most one reusable pattern were sufficient.
- Record the gaps that still force broad repository scanning or require harness-behavior updates.
- Each pilot records whether startup succeeded without target-repo harness artifacts.

## Evidence

- none
