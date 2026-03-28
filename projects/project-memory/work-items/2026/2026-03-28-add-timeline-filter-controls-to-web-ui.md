---
date: 2026-03-28
recorded_at: 2026-03-28T00:00:00.000Z
project: project-memory
topic: add-timeline-filter-controls-to-web-ui
source: agent
status: active
work_item_state: open
---
# Work Item

## Summary

Add visible filter controls to the Web timeline so project, type, and status filtering can be changed directly from the page.

## Outcome

The Web timeline page exposes explicit filter controls that map onto the existing query-parameter-based filtering model, preserve shareable URLs, keep active filter state visible, and do not change the shared-core filtering semantics.

## Provenance

- ad-hoc: User requested a dedicated follow-up work-item after confirming that timeline filtering exists only through URL/query parameters and lacks visible UI controls.

## Dependencies

- work-item:project-memory:2026-03-22:design-read-only-web-interface-baseline
- work-item:project-memory:2026-03-22:implement-web-timeline-view
- work-item:project-memory:2026-03-22:implement-web-filters

## Context

- decision:project-memory:2026-03-14:read-only-web-interface
- canonical-doc:project-memory:document-model:document-model

## Verification

- Render explicit filter controls on the timeline page for project, document type, and status.
- Keep the controls synchronized with the existing query-parameter contract instead of introducing a separate client-side filter state.
- Preserve shareable filtered URLs and browsing continuity into exact document views and back.
- Support clear or reset behavior from the same UI surface without hiding the current active filter state.
- Keep unmatched-filter and empty-repository states deterministic after the new controls are added.

## Evidence

- none
