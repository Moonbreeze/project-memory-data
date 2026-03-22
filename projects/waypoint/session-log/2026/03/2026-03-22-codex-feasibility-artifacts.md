---
date: 2026-03-22
recorded_at: 2026-03-22T00:00:00.000Z
project: waypoint
topic: codex-feasibility-artifacts
source: agent
status: active
---
# Session Note

## Summary

Recorded the missing manual feasibility artifacts for `codex app-server` by capturing CLI help, generated protocol schemas and TypeScript bindings, and a real stdio handshake through initialize, thread creation, and turn start.

## Actions

- Ran `codex app-server --help` and confirmed the experimental app-server CLI exposes `generate-json-schema`, `generate-ts`, `stdio://` transport by default, optional `ws://` listen mode, and `--session-source`.
- Ran `codex app-server generate-json-schema --out /tmp/waypoint-codex-schema` and `codex app-server generate-ts --out /tmp/waypoint-codex-ts`, which generated the expected protocol artifact sets including `v2/ThreadStart*` and `v2/TurnStart*` definitions.
- Ran a real stdio JSON-RPC handshake against `codex app-server`: `initialize` returned platform metadata, `thread/start` returned a real thread id and runtime config, `turn/start` returned an in-progress turn id, and the server emitted a `thread/started` notification.
- Observed only non-fatal stderr warnings about arg0 temp-dir cleanup and PATH update permissions under the restricted environment; the protocol commands themselves still succeeded.

## Follow-up

- Approval-request, user-input, and full turn-completion event shapes still need scenario-specific validation when those flows are exercised.
- Keep using `stdio` as the supported Codex transport and leave WebSocket unsupported until a separate implementation and validation pass exists.
