---
date: 2026-03-22
recorded_at: 2026-03-22T00:00:00.000Z
project: project-memory
topic: implement-web-read-adapter
source: agent
status: active
work_item_state: open
---
# Work Item

## Summary

Create a thin Web adapter over shared core read surfaces.

## Outcome

The Web layer has typed adapter helpers that call shared core list, read, bounded-read, and later search entrypoints, normalize route and filter inputs, and expose Web-oriented view models without duplicating repository traversal or document-model logic.

## Provenance

- decision:project-memory:2026-03-14:read-only-web-interface

## Dependencies

- work-item:project-memory:2026-03-22:design-read-only-web-interface-baseline

## Context

- canonical-doc:project-memory:document-model:document-model
- canonical-doc:project-memory:reads:bounded-read-model

## Verification

- Reuse createRepositoryContext and shared core list, read, and bounded-read entrypoints from the existing tool runtime.
- Do not reimplement repository scans, path parsing, or timeline ordering inside the Web layer.
- Define typed view models for timeline rows, document detail, and future composed or search projections.
- Surface consistent not-found and invalid-read errors for Web routes.
- Keep dependency direction one-way from Web presentation code into shared core.

## Evidence

- none
