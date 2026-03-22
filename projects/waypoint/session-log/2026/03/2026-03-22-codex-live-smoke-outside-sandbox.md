---
date: 2026-03-22
recorded_at: 2026-03-22T00:00:00.000Z
project: waypoint
topic: codex-live-smoke-outside-sandbox
source: agent
status: active
---
# Session Note

## Summary

Reran Codex live smoke outside the restricted sandbox and confirmed that the earlier response-stream disconnect was environment-specific: basic and resume scenarios passed, while the approval scenario remained inconclusive because the backend auto-approved the requested command instead of surfacing an approval request.

## Actions

- Reran a direct `codex app-server` stdio probe outside the restricted sandbox and observed a complete successful turn with `agentMessage delta` events that produced `LIVE_SMOKE_CODEX_OK`, followed by `turn/completed` and thread idle status.
- Reran `npm run test:live` outside the sandbox with `LIVE_SMOKE_CODEX=1`, `LIVE_SMOKE_CODEX_RESUME=1`, `LIVE_SMOKE_CODEX_APPROVAL=1`, `LIVE_SMOKE_CODEX_APPROVAL_PROMPT='Run the shell command pwd, then reply with the exact token LIVE_SMOKE_CODEX_APPROVAL_OK and nothing else.'`, and `LIVE_SMOKE_TIMEOUT_MS=120000`.
- Confirmed that the Codex basic live-smoke scenario passed and the Codex restart/resume scenario passed outside the sandbox.
- Observed that the Codex approval scenario executed `/bin/bash -lc pwd` and completed with `LIVE_SMOKE_CODEX_APPROVAL_OK`, but no explicit approval request surfaced in the transcript, so the test failed only on the approval-request expectation rather than on command execution or final completion.

## Follow-up

- Treat the earlier `Operation not permitted (os error 1)` Codex stream disconnect as a restricted-environment issue, not as the general outside-sandbox behavior.
- If approval smoke must pass, choose or design a stricter Codex approval prompt or environment policy that reliably surfaces an approval request instead of auto-approving the candidate operation.
- Claude live smoke still remains unverified in this workspace because Claude live flags and credentials were not enabled for this run.
