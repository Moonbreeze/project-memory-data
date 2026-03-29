---
date: 2026-03-29
recorded_at: 2026-03-29T09:47:10.030Z
project: project-memory
topic: implement-exact-document-view-ux-follow-up
source: agent
status: active
work_item_state: open
---
# Work Item

## Summary

Refine the read-only Web exact document page UX after the baseline route and search return flow are in place.

## Outcome

The Web UI exact document page has a clearer reading hierarchy, better navigation context when opened from timeline or search, and a more deliberate presentation of metadata and rendered body content while remaining strictly read-only and aligned with shared-core document semantics.

## Provenance

- ad-hoc: Split from the current hands-on review of the Web UI after validating search behavior and identifying follow-up UX improvements for the exact document screen that should not be folded into unrelated search or testing slices.

## Dependencies

- work-item:project-memory:2026-03-22:implement-web-document-view
- work-item:project-memory:2026-03-22:implement-search-in-web-ui

## Context

- canonical-doc:project-memory:web-ui:read-only-web-ui-guidance
- canonical-doc:project-memory:document-model:document-model

## Verification

- Improve the information hierarchy of the exact document page so navigation context, title, metadata, and rendered body feel intentionally ordered rather than mechanically stacked.
- Refine the timeline/search return context so the page makes the browsing origin and available way back clear without introducing Web-only read semantics.
- Rework metadata and body presentation only as a UX projection over existing managed document fields and rendered Markdown rather than by changing shared-core document meaning.
- Keep the exact document route strictly read-only and preserve deterministic fallback behavior for missing or invalid managed documents.

## Evidence

- none
