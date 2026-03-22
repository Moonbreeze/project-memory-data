---
date: 2026-03-22
recorded_at: 2026-03-22T09:37:21.270Z
project: claude-remote
topic: hard-rename-to-waypoint
source: agent
status: archived
---
# Decision

## Context

A draft naming decision already established `Waypoint` as the preferred future product/runtime name while explicitly deferring a full repository/package rename. The project has since stabilized on the provider-neutral runtime architecture, the remaining migration backlog is explicit, and continuing to defer the hard rename keeps `claude-remote` embedded in package metadata, persistence defaults, protocol client identity, tests, and project-memory naming. That drift now has a concrete execution cost and should be resolved by an explicit rename decision instead of staying as an open-ended future idea.

## Decision

Proceed with a full hard rename from `claude-remote` to `Waypoint` across repository identity, package metadata, runtime naming, and managed project terminology. Execute the rename with explicit backward-compatibility handling for persisted state and any other user-facing paths that currently embed `claude-remote`.

## Consequences

- The rename work should update repository/package identity, user-facing descriptions, protocol client identity, test fixtures, and any remaining runtime strings so the active codebase no longer presents mixed `claude-remote` and `Waypoint` naming.
- Persistence defaults must not strand existing users on the old `~/.claude-remote/...` path; the implementation must include a safe discovery or migration strategy before switching defaults.
- The project-memory backlog item `hard-rename-to-waypoint` can move from blocked to ready because the required follow-up decision now exists.
- The earlier draft `runtime-name` decision is superseded as the active source of truth for naming direction and should no longer be treated as the controlling decision.
- If the rename is intended to include project-memory project slug or other managed naming surfaces, that migration must be handled deliberately rather than assumed to follow automatically from code changes.

## Stable Guidance Review

- Outcome: updated
- Summary: Reviewed current stable guidance and updated the stable guidance in the same change slice.
