---
date: 2026-04-20
recorded_at: 2026-04-20T13:21:55.730Z
project: agent-context
topic: define-external-agent-context-entrypoint
source: agent
status: active
work_item_state: open
---
# Work Item

## Summary

Define a generalized external entrypoint into agent-context that does not require changes in the target repository.

## Outcome

The sidecar knowledge layer can be connected to arbitrary external projects outside direct repository control.

## Provenance

- ad-hoc: Initial implementation planning for the agent-context MVP based on the agreed documentation model and curation approach.

## Dependencies

- work-item:agent-context:2026-04-20:write-start-bootstrap-flow

## Context

- canonical-doc:agent-context:2026-04-20:trial-mode
- canonical-doc:agent-context:2026-04-20:agent-context-overview
- canonical-doc:agent-context:2026-04-20:platform-neutral-curation

## Verification

- One bootstrap entrypoint exists that is not tied to a specific repository.
- The entrypoint explains how to connect a target project to agent-context.
- An agent can start bootstrap without editing the target repository.
- The approach works for projects hosted in other environments.

## Evidence

- none
