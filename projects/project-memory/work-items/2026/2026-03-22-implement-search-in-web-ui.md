---
date: 2026-03-22
recorded_at: 2026-03-22T00:00:00.000Z
project: project-memory
topic: implement-search-in-web-ui
source: agent
status: active
work_item_state: open
---
# Work Item

## Summary

Implement the approved search experience for the read-only Web UI.

## Outcome

The Web UI exposes a search route and results page that use the existing shared-core search behavior with the approved query semantics, result ordering, excerpt rendering, and navigation into exact document pages.

## Provenance

- decision:project-memory:2026-03-14:read-only-web-interface

## Dependencies

- work-item:project-memory:2026-03-22:design-search-in-web-ui
- work-item:project-memory:2026-03-22:implement-web-runtime-shell
- work-item:project-memory:2026-03-22:implement-web-read-adapter
- work-item:project-memory:2026-03-22:implement-web-document-view

## Context

- canonical-doc:project-memory:reads:bounded-read-model
- decision:project-memory:2026-03-17:document-timeline-and-latest-first-query-defaults

## Verification

- Connect the search input and result list to the existing shared-core search surface.
- Render excerpts and navigation into exact document views.
- Preserve search parameters in URLs for repeatable searches.
- Keep result ordering aligned with the approved search design.
- Avoid introducing a separate search index or background sync layer.

## Evidence

- none
