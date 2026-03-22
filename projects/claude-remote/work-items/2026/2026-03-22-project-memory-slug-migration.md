---
date: 2026-03-22
recorded_at: 2026-03-22T00:00:00.000Z
project: claude-remote
topic: project-memory-slug-migration
source: user
status: archived
work_item_state: canceled
---
# Work Item

## Summary

Deliberately migrate project-memory naming surfaces from the legacy `claude-remote` project slug to a Waypoint-aligned slug without losing backlog, decisions, verification history, or topic references.

## Outcome

The managed knowledge base uses a Waypoint-aligned project slug and updated locators, with an explicit migration path for existing work items, decisions, session notes, verification records, and any cross-document references that currently depend on `claude-remote`.

## Provenance

- ad-hoc: User requested a dedicated follow-up item to migrate the managed project-memory naming surfaces from the legacy `claude-remote` slug after the Waypoint hard rename.

## Dependencies

- none

## Context

- decision:claude-remote:2026-03-22:hard-rename-to-waypoint
- decision:claude-remote:2026-03-22:waypoint-prerelease-persistence-break
- session-note:claude-remote:2026-03-22:hard-rename-to-waypoint

## Verification

- Decide the target project-memory slug and document the migration strategy before mutating managed records.
- Inventory which managed documents, locators, and cross-document references currently depend on the `claude-remote` slug.
- Execute the migration without orphaning active work items, decisions, verification results, or session history.
- Verify that planning and topic entrypoints resolve correctly after the slug migration on the new project surface.

## Evidence

- none
