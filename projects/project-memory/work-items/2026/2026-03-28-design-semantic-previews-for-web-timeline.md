---
date: 2026-03-28
recorded_at: 2026-03-28T00:00:00.000Z
project: project-memory
topic: design-semantic-previews-for-web-timeline
source: agent
status: active
work_item_state: open
---
# Work Item

## Summary

Define compact semantic preview rules for Web timeline rows so the timeline is informative for humans without expanding each row into a full document view.

## Outcome

Project-memory has an explicit design for type-aware semantic previews in the Web timeline, including which content fields to surface per document type, how preview text relates to metadata, and how the row model stays compact and scan-friendly on desktop and mobile.

## Provenance

- ad-hoc: Split from the current Web UI UX discussion so semantic timeline previews can be designed as a separate slice before continuing layout and filter refinements.

## Dependencies

- work-item:project-memory:2026-03-22:design-read-only-web-interface-baseline
- work-item:project-memory:2026-03-22:implement-web-timeline-view

## Context

- decision:project-memory:2026-03-14:read-only-web-interface
- canonical-doc:project-memory:document-model:document-model

## Verification

- Define type-aware preview rules for timeline rows instead of showing metadata alone or full document bodies.
- Specify which compact semantic content should be shown for at least session-note, verification-result, decision, work-item, runbook, canonical-doc, and provider-note rows.
- Keep document metadata as secondary context rather than the primary content surface of each row.
- Preserve latest-first scanability and compact density on desktop and mobile timeline layouts.
- Avoid introducing a second persisted summary field model when previews can be derived from existing managed document structure.

## Evidence

- none
