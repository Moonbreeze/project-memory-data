---
date: 2026-03-22
recorded_at: 2026-03-22T00:00:00.000Z
project: waypoint
topic: waypoint-prerelease-persistence-break
source: agent
status: active
---
# Decision

## Context

The Waypoint hard-rename slice is being executed before any public release. The current JSON persistence under `~/.claude-remote/sessions.json` is disposable prerelease state, and preserving automatic discovery or migration of that path adds complexity without protecting real users.

## Decision

Execute the Waypoint hard rename as a prerelease breaking change: switch the default persistence path directly to `~/.waypoint/sessions.json` and do not implement compatibility discovery or automatic migration from the old `~/.claude-remote` path.

## Consequences

- Existing prerelease persistence files under `~/.claude-remote` may be deleted or ignored without migration support.
- The runtime must still bootstrap cleanly when the new persistence file does not exist yet, creating state only on first save.
- The hard-rename work item verification no longer requires a compatibility path for persisted state.
- The earlier `hard-rename-to-waypoint` decision remains the naming direction, but its compatibility requirement is superseded by this prerelease persistence decision.

## Stable Guidance Review

- Outcome: updated
- Summary: Reviewed current stable guidance and updated the stable guidance in the same change slice.
- Note: Migrated the active prerelease persistence decision onto the authoritative waypoint project surface without changing guidance.
