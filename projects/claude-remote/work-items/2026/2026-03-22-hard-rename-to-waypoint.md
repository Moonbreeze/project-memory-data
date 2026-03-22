---
date: 2026-03-22
recorded_at: 2026-03-22T09:35:27.368Z
project: claude-remote
topic: hard-rename-to-waypoint
source: agent
status: active
work_item_state: blocked
---
# Work Item

## Summary

Execute a full hard rename from `claude-remote` to `Waypoint` across repository identity, package metadata, runtime defaults, protocol client identity, and project-memory naming surfaces.

## Outcome

The project uses `Waypoint` consistently for repository/package/runtime identity, existing users retain access to persisted session state through an explicit compatibility path, and naming drift between code, docs, protocol metadata, and project-memory is removed.

## Provenance

- decision:claude-remote:2026-03-14:runtime-name

## Dependencies

- none

## Context

- decision:claude-remote:2026-03-14:runtime-name

## Verification

- Rename repository/package-facing identifiers such as `package.json`, lockfile metadata, user-facing descriptions, and protocol client identity without leaving mixed `claude-remote`/`Waypoint` branding in the active runtime path.
- Introduce and verify an explicit persistence-path compatibility strategy so existing `~/.claude-remote/...` state is discovered or migrated safely before switching defaults to a `Waypoint` path.
- Update tests and temporary-path fixtures so the suite no longer encodes the old project name except where backward-compatibility behavior is under test.
- Define and execute the project-memory migration strategy for project slug/topic references if the rename is intended to extend to the managed knowledge base.
- Run `npm run build` and the narrowest relevant test subsets, then broaden verification once rename-related changes pass.

## Evidence

- none
