---
date: 2026-06-27
recorded_at: 2026-06-27T11:46:38.150Z
project: agent-context
topic: define-external-agent-context-entrypoint
source: agent
status: active
---
# Session Note

## Summary

Defined an explicit external bootstrap entrypoint for arbitrary target repositories and aligned runtime guidance around resolved `project-memory` identifiers or equivalent context handles before bounded startup.

## Actions

- Added `EXTERNAL_BOOTSTRAP_ENTRYPOINT.md` as the single authoring-source bootstrap contract for arbitrary target repositories.
- Updated `README.md`, `RUNBOOKS/WORK_ITEM_ORCHESTRATION.md`, and `instructions.local.md` to require resolving the target project's `project-memory` identifier or equivalent context handle before bounded reads.
- Updated the `project-memory` and `opencode-work-item-orchestration` ai-inst modules and rebuilt `CLAUDE.md` so generated instructions no longer rely on `project = directory name` assumptions.

## Follow-up

- Use the explicit external bootstrap entrypoint as the starting contract for future pilot and routing slices when external project binding is relevant.
