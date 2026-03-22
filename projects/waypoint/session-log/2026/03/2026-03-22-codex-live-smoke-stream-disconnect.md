---
date: 2026-03-22
recorded_at: 2026-03-22T00:00:00.000Z
project: waypoint
topic: codex-live-smoke-stream-disconnect
source: agent
status: active
---
# Session Note

## Summary

Ran Codex live smoke with explicit `LIVE_SMOKE_*` flags and confirmed the tests fail after `turn/start` because the real Codex backend disconnects its response stream under the current environment, not because the live scenarios are still disabled.

## Actions

- Ran `npm run test:live` with `LIVE_SMOKE_CODEX=1`, `LIVE_SMOKE_CODEX_RESUME=1`, `LIVE_SMOKE_CODEX_APPROVAL=1`, `LIVE_SMOKE_CODEX_APPROVAL_PROMPT='Run the shell command pwd, then reply with the exact token LIVE_SMOKE_CODEX_APPROVAL_OK and nothing else.'`, and `LIVE_SMOKE_TIMEOUT_MS=120000`.
- Observed that the Codex basic, approval, and resume live-smoke tests all started real turns but failed before any successful model output, while Claude scenarios remained skipped because no Claude live flags were enabled.
- Ran a direct `codex app-server` stdio debug session and confirmed the backend emits `thread/status/changed`, `turn/started`, and then repeated `error` notifications with `message: Reconnecting... N/5` and `additionalDetails: stream disconnected before completion: Operation not permitted (os error 1)`.
- Confirmed the repository worktree stayed clean during the diagnostic run.

## Follow-up

- If live Codex smoke must pass in this environment, investigate what in the current local Codex runtime or sandbox is causing the response stream disconnection after `turn/start`.
- If the issue reproduces outside the current restricted environment, treat it as a real Codex/backend integration bug rather than a missing live-var problem.
- If Claude live smoke should also be exercised, separate Claude credential setup from this Codex stream-disconnect issue so the two failure modes do not get conflated.
