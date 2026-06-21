---
date: 2026-04-20
recorded_at: 2026-04-20T13:21:37.920Z
project: agent-context
topic: define-context-curator-contract
source: agent
status: active
work_item_state: done
---
# Work Item

## Summary

Define the platform-neutral context-curator contract as inputs, outputs, non-goals, and bounded project-context assumptions.

## Outcome

Context-curator is specified without coupling the model to a single vendor workflow and without assuming repo-local sidecar knowledge as the project truth source.

## Provenance

- ad-hoc: Initial implementation planning for the agent-context MVP, later aligned with the authoring-repo and project-memory split.

## Dependencies

- work-item:agent-context:2026-04-20:scaffold-agent-context-structure

## Context

- canonical-doc:agent-context:2026-06-21:context-curator-model
- canonical-doc:agent-context:2026-06-21:platform-neutral-curation
- decision:agent-context:2026-06-21:authoring-repo-project-memory-split
- decision:agent-context:2026-04-20:context-curator-platform-neutral

## Verification

- CURATION_CONTRACT.md is created.
- The contract describes inputs, outputs, non-goals, and trigger conditions.
- The output shape is standardized as Start here / Also inspect / Pitfalls / Verify.
- The contract assumes bounded project-specific context comes from project-memory or an equivalent adapter surface rather than from mandatory repo-local sidecar files.

## Evidence

- session-note:agent-context:2026-06-21:define-context-curator-contract
- verification-result:agent-context:2026-06-21:define-context-curator-contract
