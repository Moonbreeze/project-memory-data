---
date: 2026-03-22
recorded_at: 2026-03-22T00:00:00.000Z
project: waypoint
topic: codex-app-server
source: agent
status: active
---
# Provider Note

## Overview

Treat `codex app-server` as a JSON-RPC backend over `stdio` for the migrated runtime. The repository now has provider tests, live smoke hooks, and a recorded feasibility artifact set covering CLI help, generated protocol bindings, and a real stdio handshake through `initialize`, `thread/start`, and `turn/start`.

## Constraints

- `stdio` is the only supported Codex transport in this repository today.
- The recorded feasibility handshake observed `initialize`, `thread/start`, `turn/start`, and a `thread/started` notification, but it did not exercise approval requests, user-input requests, or the full turn-completion event stream.
- WebSocket transport remains unsupported and must not be treated as implemented or configurable.
- Local `codex app-server` invocations may emit non-fatal warnings about failing to update PATH or clean up stale arg0 temp dirs under restricted permissions.

## Guidance

- Use the recorded feasibility artifacts from 2026-03-22 as the baseline contract evidence for Codex integration instead of treating the protocol as unvalidated.
- Expect a successful `turn/start` request to return an in-progress turn first; additional completion, plan, approval, or command-stream events must be validated separately depending on scenario.
- Use `npm run test:live` with explicit `LIVE_SMOKE_CODEX*` flags for opt-in real-backend smoke checks; without those flags the suite should skip safely.
- Reintroduce any non-stdio transport only after a separate validation pass confirms the contract and a real client implementation exists.
