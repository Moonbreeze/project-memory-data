---
date: 2026-03-29
recorded_at: 2026-03-29T11:09:47.733Z
project: project-memory
topic: web-server-lifecycle-and-public-linking
source: agent
status: active
---
# Decision

## Context

The read-only Web UI already existed as a standalone process entrypoint, but lifecycle management, singleton semantics, and link generation were not defined as shared-core behavior consumable equally by CLI and MCP. The lifecycle model needed to support deterministic start, stop, and status operations keyed by PROJECT_MEMORY_ROOT while separating local bind behavior from externally visible public links.

## Decision

Manage the read-only Web server through shared-core lifecycle operations that own start, stop, status, singleton runtime records, and link generation. The singleton key is PROJECT_MEMORY_ROOT plus bind host and port. Public links are derived only from explicit configuration, with PROJECT_MEMORY_WEB_PUBLIC_BASE_URL as the source of truth. CLI may optionally prompt for a missing public base URL only in TTY flows, while MCP remains fully non-interactive. Best-effort external-address discovery such as dig may be surfaced only as a suggestion and never as implicit truth or silently persisted configuration.

## Consequences

- CLI and MCP stay thin adapters over the same shared-core Web lifecycle contract instead of implementing separate runtime semantics.
- Repeated start requests for the same memory root and bind configuration are idempotent, while different memory roots are not conflated.
- Returned local links remain usable even when the server binds to wildcard addresses, because the lifecycle result projects a navigable local URL separately from the raw bind host.
- Public links are explicit and reviewable because they come from PROJECT_MEMORY_WEB_PUBLIC_BASE_URL or an explicit override rather than inferred network state.
- MCP lifecycle calls remain deterministic because they never block on prompts or interactive public-URL setup.
- Stale runtime-file cleanup becomes part of the shared lifecycle contract rather than an adapter-specific recovery behavior.

## Stable Guidance Review

- Outcome: reviewed-no-change
- Summary: Reviewed current stable guidance and determined no update was required.
