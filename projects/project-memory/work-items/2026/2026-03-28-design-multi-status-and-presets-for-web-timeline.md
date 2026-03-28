---
date: 2026-03-28
recorded_at: 2026-03-28T00:00:00.000Z
project: project-memory
topic: design-multi-status-and-presets-for-web-timeline
source: agent
status: active
work_item_state: open
---
# Work Item

## Summary

Define Web timeline support for viewing multiple statuses at once and for future preset links such as backlog-oriented views.

## Outcome

Project-memory has an explicit design for multi-status filtering and preset semantics in the Web timeline, including a shareable URL contract, UX guidance for compact controls that work on desktop and mobile, and the relationship between presets, status filters, and ordering semantics.

## Provenance

- ad-hoc: Split from the current Web UI UX discussion so multi-status timeline filtering and preset semantics can be designed as a separate follow-up instead of expanding the current layout and basic-filter slice.

## Dependencies

- work-item:project-memory:2026-03-22:design-read-only-web-interface-baseline
- work-item:project-memory:2026-03-22:implement-web-timeline-view
- work-item:project-memory:2026-03-28:add-timeline-filter-controls-to-web-ui

## Context

- decision:project-memory:2026-03-14:read-only-web-interface
- decision:project-memory:2026-03-17:document-timeline-and-latest-first-query-defaults
- canonical-doc:project-memory:document-model:document-model

## Verification

- Define a shareable Web query contract for selecting multiple document statuses at once.
- Explain why the initial UX should avoid relying on a native select-multiple control even though multiple status values are supported.
- Define how future preset links such as backlog views interact with multi-status filters, ordering, and any project scoping defaults.
- Keep the future controls compact and usable on both desktop and mobile timeline layouts.
- Avoid changing shared-core meaning implicitly; document where Web-only preset behavior stops and shared-core query semantics remain authoritative.

## Evidence

- none
