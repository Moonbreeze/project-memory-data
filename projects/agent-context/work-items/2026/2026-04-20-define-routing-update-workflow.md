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

Define how real-task findings update project-memory versus reusable authoring materials after new stable routes are discovered.

## Outcome

Project-specific truth and generic behavior patterns feed back into the correct layer without mixing runtime memory records with authoring repo documents.

## Provenance

- ad-hoc: Initial implementation planning for the agent-context MVP, now reframed around the authoring-repo and project-memory split.

## Dependencies

- work-item:agent-context:2026-04-20:create-task-routing-index
- work-item:agent-context:2026-04-20:seed-initial-recipes

## Context

- canonical-doc:agent-context:2026-06-21:task-routing
- canonical-doc:agent-context:2026-06-21:documentation-model
- decision:agent-context:2026-06-21:authoring-repo-project-memory-split

## Verification

- The workflow states when project-memory routing or current-truth records should be updated.
- The workflow states when reusable authoring recipes, templates, or modules should be created or edited in agent-context.
- The process keeps project-specific truth separate from generic behavior patterns.

## Evidence

- none
