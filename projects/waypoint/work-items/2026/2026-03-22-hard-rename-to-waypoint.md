---
date: 2026-03-22
recorded_at: 2026-03-22T00:00:00.000Z
project: waypoint
topic: hard-rename-to-waypoint
source: agent
status: active
work_item_state: done
---
# Work Item

## Summary

Execute a full prerelease hard rename from `claude-remote` to `Waypoint` across repository identity, package metadata, runtime defaults, protocol client identity, and rename-sensitive test fixtures.

## Outcome

The project uses `Waypoint` consistently for repository/package/runtime identity, the default persisted state path is `~/.waypoint/sessions.json`, and prerelease persistence under the old `~/.claude-remote` path is intentionally left without compatibility handling.

## Provenance

- decision:waypoint:2026-03-22:hard-rename-to-waypoint

## Dependencies

- none

## Context

- decision:waypoint:2026-03-22:hard-rename-to-waypoint
- decision:waypoint:2026-03-22:waypoint-prerelease-persistence-break

## Verification

- Rename repository/package-facing identifiers such as `package.json`, lockfile metadata, user-facing descriptions, and protocol client identity without leaving mixed `claude-remote`/`Waypoint` branding in the active runtime path.
- Switch the default persistence path to `~/.waypoint/sessions.json` without adding discovery or migration support for the old prerelease `~/.claude-remote` path.
- Update tests and temporary-path fixtures so the suite no longer encodes the old project name in active rename-sensitive scenarios.
- Run `npm run build` and the narrowest relevant test subset for config, persistence bootstrap, session persistence, and Codex initialization.

## Evidence

- session-note:waypoint:2026-03-22:hard-rename-to-waypoint
- verification-result:waypoint:2026-03-22:hard-rename-to-waypoint
