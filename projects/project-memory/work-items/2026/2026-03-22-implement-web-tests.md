---
date: 2026-03-22
recorded_at: 2026-03-22T00:00:00.000Z
project: project-memory
topic: implement-web-tests
source: agent
status: active
work_item_state: open
---
# Work Item

## Summary

Add automated coverage for the Web runtime, routes, adapter behavior, and baseline read-only flows.

## Outcome

The repository has automated tests for the Web surface that cover route behavior, latest-first ordering, filters, exact document rendering, Markdown rendering, and deterministic error states using the existing project-memory test patterns.

## Provenance

- decision:project-memory:2026-03-14:read-only-web-interface

## Dependencies

- work-item:project-memory:2026-03-22:implement-web-runtime-shell
- work-item:project-memory:2026-03-22:implement-web-read-adapter
- work-item:project-memory:2026-03-22:implement-web-timeline-view
- work-item:project-memory:2026-03-22:implement-web-filters
- work-item:project-memory:2026-03-22:implement-web-document-view
- work-item:project-memory:2026-03-22:implement-web-markdown-rendering
- work-item:project-memory:2026-03-22:implement-web-navigation-and-states

## Context

- canonical-doc:project-memory:document-model:document-model

## Verification

- Cover Web routes and adapter integration for timeline, filters, and exact document view.
- Verify that timeline ordering matches the existing latest-first date, recorded_at, and relativePath semantics.
- Verify that filter parameters map correctly onto shared-core queries.
- Verify Markdown rendering and deterministic fallback states for missing or invalid documents.
- Reuse the repository's existing external memory repo test patterns instead of inventing a separate fixture model.

## Evidence

- none
