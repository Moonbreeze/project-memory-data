---
date: 2026-03-22
recorded_at: 2026-03-22T00:00:00.000Z
project: waypoint
topic: codex-live-smoke-outside-sandbox
source: agent
status: active
---
# Verification Result

## Scope

Codex live smoke rerun outside the restricted sandbox

## Steps

- Ran a direct `codex app-server` stdio probe outside the sandbox and observed a complete successful turn that emitted `agentMessage delta` chunks for `LIVE_SMOKE_CODEX_OK`, followed by `turn/completed` and idle thread status.
- Ran `npm run test:live` outside the sandbox with `LIVE_SMOKE_CODEX=1`, `LIVE_SMOKE_CODEX_RESUME=1`, `LIVE_SMOKE_CODEX_APPROVAL=1`, `LIVE_SMOKE_CODEX_APPROVAL_PROMPT='Run the shell command pwd, then reply with the exact token LIVE_SMOKE_CODEX_APPROVAL_OK and nothing else.'`, and `LIVE_SMOKE_TIMEOUT_MS=120000`.
- Observed the Codex basic live-smoke scenario pass.
- Observed the Codex restart/resume live-smoke scenario pass.
- Observed the Codex approval live-smoke scenario execute the command and return `LIVE_SMOKE_CODEX_APPROVAL_OK`, but fail the test because no `Approval requested` transcript entry appeared.

## Result

Outside the restricted sandbox, Codex live smoke no longer reproduces the response-stream disconnect: basic and resume pass. The remaining failing scenario is approval-only and is currently inconclusive because the backend auto-approves the tested command instead of surfacing an approval request.
