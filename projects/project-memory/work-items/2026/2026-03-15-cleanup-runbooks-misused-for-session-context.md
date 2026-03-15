---
date: 2026-03-15
project: project-memory
topic: cleanup-runbooks-misused-for-session-context
source: agent
status: active
work_item_state: open
---
# Work Item

## Summary

Audit and clean up runbooks that currently contain session chronology or execution context instead of repeatable procedures.

## Outcome

Runbooks once again represent repeatable operational procedures, while session history and execution context move into the correct managed document types.

## Provenance

- ad-hoc: Documentation review found older runbooks that were used to store session context before work-items and the current document taxonomy were established.

## Dependencies

- work-item:project-memory:2026-03-15:expand-managed-document-archive-coverage

## Context

- none

## Verification

- Identify runbooks whose primary content is session history or transient execution context.
- Decide case by case whether each item should be rewritten, split, migrated to another document type, or archived.
- Leave the remaining runbooks aligned with the current taxonomy and operating model.

## Evidence

- none
