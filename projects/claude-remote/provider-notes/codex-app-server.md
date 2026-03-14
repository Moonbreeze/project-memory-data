---
date: 2026-03-12
project: claude-remote
topic: codex-app-server
source: agent
status: active
---
# Provider Note

## Overview

The repository currently treats codex app-server as a JSON-RPC backend over stdio. A minimal client and mocked protocol tests exist, the Codex provider covers thread/start, thread/resume, turn/start, turn/interrupt, approval routing, and result/error handling, and the live smoke suite can exercise the real local codex CLI when enabled.

## Constraints

- stdio is the only supported Codex transport in this repository today.
- There is no checked-in manual artifact set from the original feasibility-gate commands yet.
- The real live event-stream shape has not been fully recorded as a manual feasibility report in-repo.
- WebSocket transport remains unsupported and must not be treated as implemented.

## Guidance

- Reintroduce any non-stdio transport only after a separate validation pass confirms the contract and a real client implementation exists.
- To fully close the original feasibility gate, manually run and record codex app-server --help, codex app-server generate-json-schema --out <tmp-dir>, codex app-server generate-ts --out <tmp-dir>, and a minimal live handshake covering initialize, thread creation or resume, turn start, and representative notifications or requests.
- Until those artifacts are recorded, describe Codex integration as validated by code, tests, and live smoke, but not yet fully documented by a manual feasibility report.
- If live Codex checks fail only inside a restricted sandbox and pass outside it, treat that as an environment limitation unless stronger evidence indicates a product regression.
