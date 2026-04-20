---
date: 2026-04-20
recorded_at: 2026-04-20T13:21:47.939Z
project: agent-context
topic: scaffold-context-curator-platform-adapters
source: agent
status: active
work_item_state: open
---
# Work Item

## Summary

Add templates or scripts to scaffold platform-specific adapter skeletons for context-curator.

## Outcome

New Claude, Codex, and Cursor adapters can be created consistently on top of the shared curation contract.

## Provenance

- ad-hoc: Initial implementation planning for the agent-context MVP based on the agreed documentation model and curation approach.

## Dependencies

- work-item:agent-context:2026-04-20:define-context-curator-contract

## Context

- canonical-doc:agent-context:2026-04-20:context-curator-model
- canonical-doc:agent-context:2026-04-20:platform-neutral-curation
- decision:agent-context:2026-04-20:context-curator-platform-neutral

## Verification

- The scaffold creates skeletons for at least Claude, Codex, and Cursor.
- The shared contract is not duplicated manually across platform adapters.
- Platform-specific files stay separated from the canonical model.
- The generated output includes a short list of remaining manual steps.

## Evidence

- none
