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

Run the model on several real tasks to validate whether agent-context reduces startup context cost.

## Outcome

The team has evidence about whether START, ENTRYPOINTS, and optional RECIPES are enough for low-cost task startup.

## Provenance

- ad-hoc: Initial implementation planning for the agent-context MVP based on the agreed documentation model and curation approach.

## Dependencies

- work-item:agent-context:2026-04-20:write-start-bootstrap-flow
- work-item:agent-context:2026-04-20:create-task-routing-index
- work-item:agent-context:2026-04-20:seed-initial-recipes
- work-item:agent-context:2026-04-20:write-system-map
- work-item:agent-context:2026-04-20:define-context-curator-contract
- work-item:agent-context:2026-04-20:define-external-agent-context-entrypoint

## Context

- canonical-doc:agent-context:2026-04-20:agent-context-overview
- canonical-doc:agent-context:2026-04-20:task-routing
- canonical-doc:agent-context:2026-04-20:context-curator-model

## Verification

- Run three to five real task trials.
- For each task, determine whether START plus ENTRYPOINTS and at most one RECIPE were sufficient.
- Record the gaps that still force broad repository scanning.

## Evidence

- none
