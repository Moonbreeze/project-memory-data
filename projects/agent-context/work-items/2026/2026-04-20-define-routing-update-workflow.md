---
date: 2026-04-20
recorded_at: 2026-04-20T13:22:03.758Z
project: agent-context
topic: define-routing-update-workflow
source: agent
status: active
work_item_state: open
---
# Work Item

## Summary

Define how routing documents are updated after real tasks reveal new stable navigation paths.

## Outcome

New stable routes are fed back into ENTRYPOINTS and RECIPES without introducing backlog or session-log layers.

## Provenance

- ad-hoc: Initial implementation planning for the agent-context MVP based on the agreed documentation model and curation approach.

## Dependencies

- work-item:agent-context:2026-04-20:create-task-routing-index
- work-item:agent-context:2026-04-20:seed-initial-recipes

## Context

- canonical-doc:agent-context:2026-04-20:task-routing
- canonical-doc:agent-context:2026-04-20:documentation-model

## Verification

- The workflow states when ENTRYPOINTS.md should be updated.
- The workflow states when RECIPES should be created or edited.
- The process does not require backlog or session-note tracking inside agent-context.

## Evidence

- none
