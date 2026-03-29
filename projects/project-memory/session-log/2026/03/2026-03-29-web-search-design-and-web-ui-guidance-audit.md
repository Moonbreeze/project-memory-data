---
date: 2026-03-29
recorded_at: 2026-03-29T06:17:04.015Z
project: project-memory
topic: web-search-design-and-web-ui-guidance-audit
source: agent
status: active
---
# Session Note

## Summary

Reviewed the current Web UI stable-guidance surface, finalized the approved design direction for on-demand Web search, and identified which recent Web UI UX decisions still lived only in work-item and session-note history.

## Actions

- Audited decision and canonical-doc coverage for the read-only Web UI and confirmed that recent sticky-shell, visible-filter, semantic-preview, and mobile-accordion refinements were not yet captured as stable guidance.
- Defined the Web search design as a dedicated `/search` route that stays a thin wrapper over shared-core search behavior with `q`, `project`, `type`, and `limit` as the shareable query contract.
- Agreed that search should remain on-demand rather than permanently expanded in the timeline shell, and that the search page should keep a visible summary while collapsing the query form after an executed search.
- Identified the existing timeline accordion as a reusable pattern candidate and framed it as a narrow Web collapsible-control primitive with separate `mobile-only` and `always` modes rather than as an oversized generic component abstraction.

## Follow-up

- Implement the approved `/search` route, result view, and return-navigation behavior in the Web UI implementation slice.
- Extract the current timeline toggle markup and styling into a reusable Web collapsible-control primitive during the search implementation work.
- Carry the remaining Web timeline follow-up design for multi-status filters and preset semantics as a separate design slice.
