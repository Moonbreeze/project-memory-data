---
date: 2026-04-20
recorded_at: 2026-04-20T13:21:12.133Z
project: agent-context
topic: write-start-bootstrap-flow
source: agent
status: active
work_item_state: done
---
# Work Item

## Summary

Define the harness bootstrap flow that starts from bounded project-memory reads rather than target-repository sidecar files.

## Outcome

An agent can begin work on a target repository by reading bounded project-memory context and then inspecting only the cited code paths.

## Provenance

- ad-hoc: Initial implementation planning for the agent-context MVP, now reframed around the authoring-repo and project-memory split.

## Dependencies

- work-item:agent-context:2026-04-20:scaffold-agent-context-structure
- work-item:agent-context:2026-04-20:define-trial-doc-metadata

## Context

- canonical-doc:agent-context:2026-06-21:agent-context-overview
- canonical-doc:agent-context:2026-06-21:trial-mode
- decision:agent-context:2026-06-21:authoring-repo-project-memory-split

## Verification

- The bootstrap flow explains which bounded project-memory entrypoint should be read first.
- The flow links task selection to planning or topic reads before broader repository inspection.
- The startup path does not depend on START.md existing in the target repository.
- The resulting flow remains compact enough to serve as a cheap bootstrap entrypoint.

## Evidence

- session-note:agent-context:2026-06-27:write-start-bootstrap-flow
- verification-result:agent-context:2026-06-27:write-start-bootstrap-flow
