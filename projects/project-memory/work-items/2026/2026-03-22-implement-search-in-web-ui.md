---
date: 2026-03-22
recorded_at: 2026-03-22T00:00:00.000Z
project: project-memory
topic: implement-search-in-web-ui
source: agent
status: active
work_item_state: done
---
# Work Item

## Summary

Implement the approved on-demand search experience for the read-only Web UI.

## Outcome

The Web UI exposes a dedicated `/search` route and results page that wrap the existing shared-core search behavior with the approved query semantics, latest-first result ordering, compact excerpts, preserved navigation into exact document pages, a compact entry point from the timeline shell, and a reusable collapsible-control primitive that supports the approved search and filter layouts.

## Provenance

- decision:project-memory:2026-03-14:read-only-web-interface

## Dependencies

- work-item:project-memory:2026-03-22:design-search-in-web-ui
- work-item:project-memory:2026-03-22:implement-web-runtime-shell
- work-item:project-memory:2026-03-22:implement-web-read-adapter
- work-item:project-memory:2026-03-22:implement-web-document-view

## Context

- canonical-doc:project-memory:reads:bounded-read-model
- canonical-doc:project-memory:web-ui:read-only-web-ui-guidance
- decision:project-memory:2026-03-17:document-timeline-and-latest-first-query-defaults
- decision:project-memory:2026-03-29:web-search-route-and-collapsible-control-pattern

## Verification

- Connect the compact search entry point and the `/search` result view to the existing shared-core search surface without introducing a separate search index or background sync layer.
- Render latest-first search results with approved excerpts and navigation into exact document views while preserving return URLs.
- Preserve `q`, `project`, `type`, and `limit` in shareable URLs for repeatable searches and avoid adding unsupported Web-only search semantics such as `status` filtering or independent ranking.
- Render the search page so the query form is available in the initial state but collapses by default after an executed search while keeping the active query scope visible.
- Extract or introduce the reusable collapsible-control primitive needed to support the approved timeline and search control layouts instead of duplicating ad hoc toggle markup.

## Evidence

- session-note:project-memory:2026-03-29:implement-search-in-web-ui
- verification-result:project-memory:2026-03-29:implement-search-in-web-ui
