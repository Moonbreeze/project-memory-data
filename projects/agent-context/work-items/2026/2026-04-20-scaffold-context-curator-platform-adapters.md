---
date: 2026-04-20
recorded_at: 2026-04-20T13:21:47.939Z
project: agent-context
topic: scaffold-context-curator-platform-adapters
source: agent
status: active
work_item_state: canceled
---
# Work Item

## Summary

Add templates or scripts to scaffold platform-specific adapters that implement the context-curator contract over bounded project-memory context.

## Outcome

New Claude, Codex, and Cursor adapters can be created consistently on top of the shared curator contract and project-memory-backed inputs.

## Provenance

- ad-hoc: Initial implementation planning for the agent-context MVP, now reframed around the authoring-repo and project-memory split.

## Dependencies

- work-item:agent-context:2026-04-20:define-context-curator-contract

## Context

- canonical-doc:agent-context:2026-06-21:context-curator-model
- canonical-doc:agent-context:2026-06-21:platform-neutral-curation
- decision:agent-context:2026-06-21:authoring-repo-project-memory-split

## Verification

- The scaffold creates skeletons for at least Claude, Codex, and Cursor.
- The shared contract is not duplicated manually across platform adapters.
- Platform-specific files expect bounded project context inputs rather than repo-local sidecar assumptions.
- The generated output includes a short list of remaining manual steps.

## Evidence

- none
