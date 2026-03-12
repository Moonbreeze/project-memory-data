---
date: 2026-03-12
project: claude-remote
topic: multi-provider-runtime-architecture
source: agent
status: active
project_commit: a9f3e30b3e57de375a441f44623a26e4cac3a3e6
---
# Decision

## Context

The repository-level migration plan defines the architectural source of truth for the post-tmux runtime. The project has already moved away from the legacy grammy + tmux + terminal-parsing path, but future work still needs stable guardrails so providers, transports, and persistence do not drift back into provider-specific coupling.

## Decision

Keep the runtime centered on a provider-neutral core built around SessionManager, provider adapters, provider-neutral AgentEvent and TransportEvent flows, and persisted session records. Raw Claude SDK messages and raw Codex app-server protocol events must remain inside provider adapters. SessionManager remains the runtime-level owner of pending request routing, while provider-local approval helpers may bridge provider callbacks to transport decisions. Codex is treated as a JSON-RPC backend over stdio only unless a separate validated implementation introduces another transport.

## Consequences

- Core and transport layers must not import Claude SDK types or Codex raw protocol types.
- Future provider work should extend provider adapters and provider-neutral event mappings instead of introducing provider-aware logic in SessionManager or transports.
- Unsupported Codex transport modes such as WebSocket must stay undocumented or explicitly marked unsupported until they are validated and implemented.
- Architecture discussions should treat MULTI_PROVIDER_REFACTOR_PLAN.md as the canonical source of truth and keep operational docs secondary to it.
