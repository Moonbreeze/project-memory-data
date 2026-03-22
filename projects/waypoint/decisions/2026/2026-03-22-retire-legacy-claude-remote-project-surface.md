---
date: 2026-03-22
recorded_at: 2026-03-22T00:00:00.000Z
project: waypoint
topic: retire-legacy-claude-remote-project-surface
source: agent
status: active
---
# Decision

## Context

The managed project-memory surface has already been recreated under the authoritative `waypoint` slug. Because the project is still prerelease, keeping the legacy `claude-remote` managed surface around provides no user-value and leaves a second active planning and documentation surface that can drift from the new project identity.

## Decision

Retire the legacy `claude-remote` project-memory surface instead of preserving it as historical source material. Archive the old managed documents, cancel and archive any non-terminal legacy work items, and treat `waypoint` as the only active project-memory project slug going forward.

## Consequences

- Future project-memory reads, writes, backlog checks, and topic entrypoints for this codebase must use `waypoint` only.
- The legacy `claude-remote` project will no longer surface active planning items or active operational guidance after the archival pass.
- Because the project is prerelease, no compatibility layer or dual-surface support is required for the old managed slug.
- Any future need to inspect the old managed records should be satisfied through the archived documents, not by reactivating the legacy project surface.

## Stable Guidance Review

- Outcome: updated
- Summary: Reviewed current stable guidance and updated the stable guidance in the same change slice.
- Note: User explicitly confirmed the legacy prerelease slug is no longer needed, so stable guidance now requires retiring the old managed surface entirely.
