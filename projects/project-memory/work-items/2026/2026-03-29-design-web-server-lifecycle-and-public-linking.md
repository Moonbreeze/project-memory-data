---
date: 2026-03-29
recorded_at: 2026-03-29T08:33:15.011Z
project: project-memory
topic: design-web-server-lifecycle-and-public-linking
source: agent
status: active
work_item_state: done
---
# Work Item

## Summary

Define the shared-core lifecycle model for the read-only Web server, including singleton start/stop/status behavior and local/public link generation for CLI and MCP consumers.

## Outcome

Project-memory has an explicit design for managing the read-only Web server through shared core operations that support CLI and MCP equally, including idempotent singleton lifecycle semantics keyed by PROJECT_MEMORY_ROOT, explicit local/public link generation, deterministic non-interactive behavior for MCP, interactive public URL setup only in CLI, and a configuration model that treats PROJECT_MEMORY_WEB_PUBLIC_BASE_URL as the source of truth while using dig-based discovery only as an optional suggestion.

## Provenance

- ad-hoc: Split from the current discussion about Web-server lifecycle management and global link generation so the shared-core design for start/stop/status, singleton behavior, and public URL handling can be evaluated as a dedicated work slice instead of being folded into unrelated Web UI work.

## Dependencies

- none

## Context

- decision:project-memory:2026-03-14:read-only-web-interface
- canonical-doc:project-memory:web-ui:read-only-web-ui-guidance

## Verification

- Define a shared core API for Web-server lifecycle operations and link generation so CLI and MCP remain thin adapters over the same behavior.
- Define singleton semantics keyed by PROJECT_MEMORY_ROOT and runtime configuration so repeated start requests are idempotent and different memory roots are not conflated.
- Keep local bind configuration separate from public URL generation by treating PROJECT_MEMORY_WEB_PUBLIC_BASE_URL as the explicit source of truth for public links.
- Allow dig-based external-address discovery only as an optional candidate suggestion and never as implicit truth or silent persisted configuration.
- Restrict interactive prompting for missing public URL configuration to CLI TTY flows and keep MCP behavior deterministic and non-interactive.
- Define the runtime state needed for start, stop, and status operations, including stale-process recovery and returned local/public URL fields.

## Evidence

- session-note:project-memory:2026-03-29:web-server-lifecycle-design-discussion
- session-note:project-memory:2026-03-29:web-server-lifecycle-implementation
- verification-result:project-memory:2026-03-29:web-server-lifecycle-verification
