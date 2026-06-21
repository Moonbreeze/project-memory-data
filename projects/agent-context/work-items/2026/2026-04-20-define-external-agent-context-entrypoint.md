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

Define how a target repository binds to its project-memory context and shared harness behavior without repo-local sidecar bootstrap files.

## Outcome

The harness can start bootstrap on arbitrary repositories by resolving the project-memory context handle and applying shared behavior-layer rules.

## Provenance

- ad-hoc: Initial implementation planning for the agent-context MVP, now reframed around the authoring-repo and project-memory split.

## Dependencies

- work-item:agent-context:2026-04-20:write-start-bootstrap-flow

## Context

- canonical-doc:agent-context:2026-06-21:trial-mode
- canonical-doc:agent-context:2026-06-21:agent-context-overview
- canonical-doc:agent-context:2026-06-21:platform-neutral-curation
- decision:agent-context:2026-06-21:authoring-repo-project-memory-split

## Verification

- One bootstrap entrypoint exists that is not tied to a specific target-repository file layout.
- The entrypoint explains how to connect or resolve a target project to the correct project-memory context.
- An agent can start bootstrap without editing the target repository.
- The approach works for projects hosted in other environments.

## Evidence

- none
