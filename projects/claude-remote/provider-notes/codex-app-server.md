---
date: 2026-03-22
recorded_at: 2026-03-22T09:30:48.256Z
project: claude-remote
topic: codex-app-server
source: agent
status: archived
---
# Provider Note

## Overview

Treat `codex app-server` as a JSON-RPC backend over `stdio` for the migrated runtime. The repository has a minimal client, mocked protocol coverage, provider tests for thread and turn flow, approval routing, result and error handling, and opt-in live smoke coverage against a real local Codex CLI.

## Constraints

- `stdio` is the only supported Codex transport in this repository today.
- There is still no checked-in manual artifact set from the original feasibility-gate commands.
- The real live event-stream shape has not yet been fully recorded as a standalone manual feasibility report.
- WebSocket transport remains unsupported and must not be treated as implemented or configurable.

## Guidance

- Keep Codex integration framed as code-validated and smoke-validated, but not fully documented by a manual feasibility report until the missing artifacts are recorded.
- To close the original feasibility gate, manually run and record `codex app-server --help`, `codex app-server generate-json-schema --out <tmp-dir>`, `codex app-server generate-ts --out <tmp-dir>`, and a minimal live handshake that captures `initialize`, thread creation or resume, `turn/start`, and representative notifications or requests.
- Reintroduce any non-stdio transport only after a separate validation pass confirms the contract and a real client implementation exists.
- If live Codex checks fail only inside a restricted sandbox and pass outside it, treat that as an environment limitation unless stronger evidence indicates a product regression.
