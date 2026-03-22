---
date: 2026-03-22
recorded_at: 2026-03-22T00:00:00.000Z
project: waypoint
topic: project-memory-slug-migration
source: agent
status: active
---
# Session Note

## Summary

Migrated the managed project-memory surface from the legacy `claude-remote` slug to the authoritative `waypoint` slug, recreated the bounded history and backlog on the new project, and verified that bounded reads now resolve on the new surface.

## Actions

- Bootstrapped the new `waypoint` managed project surface and created the `project-memory-slug` decision to document the target slug and migration strategy before mutating records.
- Recreated 23 legacy managed records from `claude-remote` under `waypoint`: 6 decisions, 1 provider note, 3 runbooks, 5 session notes, 2 verification results, and 6 work items.
- Rewrote migrated work-item dependency, context, provenance, and evidence locators from `claude-remote` to `waypoint` wherever equivalent migrated records exist.
- Verified that bounded cold-start, planning-backlog, and planning-topic entrypoints resolve on `waypoint` and that no migrated `waypoint` documents still contain legacy locator prefixes such as `decision:claude-remote` or `work-item:claude-remote`.

## Follow-up

- If the legacy `claude-remote` managed surface should be archived or pruned later, handle that as a separate cleanup pass so any remaining historical-only records are retired deliberately.
- Future project-memory reads and writes for this codebase should use the `waypoint` project slug.
