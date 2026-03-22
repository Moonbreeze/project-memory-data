---
date: 2026-03-22
recorded_at: 2026-03-22T00:00:00.000Z
project: waypoint
topic: codex-live-smoke-stream-disconnect
source: agent
status: active
---
# Verification Result

## Scope

Codex live smoke with explicit `LIVE_SMOKE_*` variables enabled in the current workspace

## Steps

- Ran `npm run test:live` with `LIVE_SMOKE_CODEX=1`, `LIVE_SMOKE_CODEX_RESUME=1`, `LIVE_SMOKE_CODEX_APPROVAL=1`, `LIVE_SMOKE_CODEX_APPROVAL_PROMPT='Run the shell command pwd, then reply with the exact token LIVE_SMOKE_CODEX_APPROVAL_OK and nothing else.'`, and `LIVE_SMOKE_TIMEOUT_MS=120000`.
- Observed 3 live Codex failures: basic, approval, and resume all reached `Codex turn started` and then failed without returning the expected smoke tokens.
- Ran a direct `codex app-server` stdio probe and captured notifications after `turn/start`: `thread/status/changed`, `turn/started`, `item/started`, `item/completed`, followed by repeated `error` notifications whose `additionalDetails` said `stream disconnected before completion: Operation not permitted (os error 1)`.
- Confirmed the failing live-smoke transcript seen by the test harness matches the backend errors: `Status`, `Codex session is active`, `Status`, `Codex turn started`, then `Reconnecting... N/5` and `Error`.

## Result

Failed Codex live smoke in this environment even with live vars enabled. The blocker is not missing `LIVE_SMOKE_*` flags: the real Codex backend starts the turn and then repeatedly disconnects its response stream with `Operation not permitted (os error 1)`, so no successful completion token is produced.
