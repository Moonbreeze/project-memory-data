---
date: 2026-03-28
recorded_at: 2026-03-28T00:00:00.000Z
project: project-memory
topic: add-timeline-filter-controls-to-web-ui
source: agent
status: active
work_item_state: done
---
# Work Item

## Summary

Add explicit timeline filter controls and a denser sticky browsing shell to the Web UI so filtering can be changed directly from the page without leaving the URL-driven read model.

## Outcome

The Web timeline exposes visible project, type, and status controls, applies them directly through shareable URLs, defaults the base timeline view to the most recent project while keeping an explicit All projects option, uses a sticky top shell for browsing context and controls, and presents a denser timeline layout without changing shared-core filtering semantics.

## Provenance

- ad-hoc: User requested a dedicated follow-up work-item after confirming that timeline filtering existed only through URL/query parameters and lacked visible UI controls.

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
- Auto-apply filter changes from the timeline UI while preserving shareable URLs and browsing continuity into exact document views and back.
- Default the base timeline route to the most recent project while keeping an explicit all-projects option available from the same control surface.
- Support clear or reset behavior from the same sticky UI surface and keep unmatched-filter and empty-repository states deterministic after the new controls are added.
- Keep the sticky header shell, wrapped filter layout, and denser timeline rows usable on both desktop and mobile.

## Evidence

- session-note:project-memory:2026-03-28:add-timeline-filter-controls-to-web-ui
- verification-result:project-memory:2026-03-28:add-timeline-filter-controls-to-web-ui
- session-note:project-memory:2026-03-28:web-timeline-semantic-previews-and-sticky-filter-accordion
- verification-result:project-memory:2026-03-28:web-timeline-semantic-previews-and-sticky-filter-accordion
