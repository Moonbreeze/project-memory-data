---
date: 2026-03-22
recorded_at: 2026-03-22T00:00:00.000Z
project: waypoint
topic: project-memory-slug
source: agent
status: active
---
# Decision

## Context

The runtime and repository have already been hard-renamed to Waypoint, but managed project-memory documents, locators, and backlog state still live under the legacy `claude-remote` project slug. Leaving managed records on the old slug would keep planning and operational context split from the renamed project identity.

## Decision

Use `waypoint` as the authoritative project-memory project slug. Migrate the active managed record set from `claude-remote` by recreating documents under `waypoint`, updating same-project locators to the new slug, and treating the legacy `claude-remote` surface as historical migration source material rather than the active planning surface.

## Consequences

- Future cold-start, topic, and planning reads should target the `waypoint` project slug.
- Work-item dependencies, context locators, and evidence locators must be rewritten to `waypoint` when equivalent migrated records exist there.
- Legacy `claude-remote` records remain as historical migration source material until any later cleanup or archival pass, but they are no longer the authoritative project surface.
- Migration verification must confirm that bounded planning and topic entrypoints resolve on `waypoint` after the document recreation pass.

## Stable Guidance Review

- Outcome: updated
- Summary: Reviewed current stable guidance and updated the stable guidance in the same change slice.
- Note: Established the authoritative managed project slug and migration strategy as new stable guidance for the renamed project.
