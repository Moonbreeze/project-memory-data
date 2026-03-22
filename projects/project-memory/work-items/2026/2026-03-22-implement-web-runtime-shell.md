---
date: 2026-03-22
recorded_at: 2026-03-22T00:00:00.000Z
project: project-memory
topic: implement-web-runtime-shell
source: agent
status: active
work_item_state: done
---
# Work Item

## Summary

Create the minimal Node/TypeScript Web runtime shell for the read-only UI.

## Outcome

The repository has a new src/web entrypoint with a minimal HTTP server, route dispatch, HTML shell, env-driven host/port configuration, and an npm script to launch the Web UI locally while delegating data reads to shared core logic.

## Provenance

- decision:project-memory:2026-03-14:read-only-web-interface

## Dependencies

- work-item:project-memory:2026-03-22:design-read-only-web-interface-baseline

## Context

- canonical-doc:project-memory:document-model:document-model
- canonical-doc:project-memory:reads:bounded-read-model

## Verification

- Add a src/web entrypoint and startup path that run in this repository's existing Node/TypeScript environment.
- Read PROJECT_MEMORY_ROOT through the shared repository context rather than through a separate Web-only configuration path.
- Provide route dispatch points for timeline and exact document views without any write actions.
- Expose documented host and port configuration for local execution.
- Keep the runtime shell thin and free of duplicated core read logic.

## Evidence

- session-note:project-memory:2026-03-22:implement-web-runtime-shell
- verification-result:project-memory:2026-03-22:implement-web-runtime-shell
