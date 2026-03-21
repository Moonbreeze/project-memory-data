---
date: 2026-03-15
recorded_at: 2026-03-15T00:00:00.000Z
project: project-memory
topic: cleanup-runbooks-misused-for-session-context
source: agent
status: archived
work_item_state: done
---
# Work Item

## Summary

Audit and clean up runbooks that currently contain session chronology, transient execution context, or misfiled baseline content instead of repeatable procedures.

## Outcome

Project-memory no longer uses active runbooks for transient planning or model baselines, and repeatable procedures are cleanly separated from canonical guidance, rationale, and execution history.

## Provenance

- ad-hoc: Documentation review found older runbooks that were used to store session context before work-items and the current document taxonomy were established.

## Dependencies

- work-item:project-memory:2026-03-15:expand-managed-document-archive-coverage

## Context

- canonical-doc:project-memory:document-model:document-model

## Verification

- Identify runbooks whose primary content is session history, transient execution context, or misfiled baseline guidance.
- Decide case by case whether each item should be rewritten, split, migrated to another document type, or archived.
- Leave the remaining active runbooks, if any, aligned with the current taxonomy and operating model.

## Evidence

- session-note:project-memory:2026-03-15:cleanup-runbooks-misused-for-session-context
- verification-result:project-memory:2026-03-15:cleanup-runbooks-misused-for-session-context
