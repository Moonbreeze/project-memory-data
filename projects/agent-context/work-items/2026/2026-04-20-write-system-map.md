---
date: 2026-04-20
recorded_at: 2026-04-20T13:21:30.377Z
project: agent-context
topic: write-system-map
source: agent
status: active
work_item_state: done
---
# Work Item

## Summary

Write the architecture and system map for the authoring repository, build pipeline, and runtime layer split.

## Outcome

Contributors can distinguish the authoring repo, generated behavior artifacts, and project-memory data surfaces without treating agent-context as a target-project sidecar.

## Provenance

- ad-hoc: Initial implementation planning for the agent-context MVP, now reframed around the authoring-repo and project-memory split.

## Dependencies

- work-item:agent-context:2026-04-20:scaffold-agent-context-structure

## Context

- canonical-doc:agent-context:2026-06-21:agent-context-overview
- canonical-doc:agent-context:2026-06-21:documentation-model
- decision:agent-context:2026-06-21:authoring-repo-project-memory-split

## Verification

- The system map covers the main authoring, build, and runtime zones.
- Each zone records a path or surface, purpose, and when it should be read or used.
- The map stays concise and does not drift into project-specific code details for unrelated repositories.

## Evidence

- session-note:agent-context:2026-06-21:write-system-map
- verification-result:agent-context:2026-06-21:write-system-map
