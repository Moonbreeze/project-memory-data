---
date: 2026-03-17
recorded_at: 2026-03-17T00:00:00.000Z
project: project-memory
topic: historical-recorded-at-backfill-strategy
source: agent
status: active
work_item_state: done
---
# Work Item

## Summary

Evaluate whether older managed documents need a historical `recorded_at` backfill strategy beyond the current deterministic date fallback.

## Outcome

Project-memory has an explicit decision about whether historical `recorded_at` backfill is required, which document types it applies to, what evidence sources are acceptable for reconstructing timestamps, and whether any migration runbook or tooling should exist.

## Provenance

- ad-hoc: Follow-up identified after introducing `recorded_at` with backward-compatible fallback ordering; the project now needs an explicit decision on whether historical same-day precision matters enough to justify backfilling older managed documents.

## Dependencies

- none

## Context

- decision:project-memory:2026-03-17:document-timeline-and-latest-first-query-defaults

## Verification

- Identify the user-facing and operational cases where midnight fallback is insufficient for older same-day documents.
- Evaluate whether git history or any other source can provide trustworthy historical intra-day timestamps for each managed document type.
- Decide whether historical backfill should be full, partial, best-effort, or intentionally skipped.
- Define whether a dedicated migration runbook or tooling is needed and what guardrails would be required before any backfill is executed.

## Evidence

- session-note:project-memory:2026-03-21:historical-recorded-at-backfill-policy
