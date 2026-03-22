---
date: 2026-03-22
recorded_at: 2026-03-22T00:00:00.000Z
project: waypoint
topic: retire-legacy-claude-remote-project-surface
source: agent
status: active
---
# Session Note

## Summary

Retired the prerelease legacy `claude-remote` managed project-memory surface after migrating the authoritative records to `waypoint`, so the old slug no longer exposes active docs or active backlog.

## Actions

- Created the `retire-legacy-claude-remote-project-surface` decision on `waypoint` to make full retirement of the old managed slug the stable prerelease policy.
- Canceled the non-terminal legacy work items on `claude-remote` because their authoritative equivalents now live under `waypoint`.
- Archived all legacy `claude-remote` work items, decisions, runbooks, provider notes, session notes, and verification results so the old project surface no longer carries active planning or active operational guidance.
- Verified that `read_cold_start` and `read_planning_backlog` on `claude-remote` return no bounded active sources while `waypoint` planning remains intact.

## Follow-up

- Use `waypoint` exclusively for future project-memory reads and writes for this codebase.
- If someone needs to inspect the legacy managed records later, use the archived `claude-remote` documents rather than reviving the old project surface.
