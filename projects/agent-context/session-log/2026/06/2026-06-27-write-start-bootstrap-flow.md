---
date: 2026-06-27
recorded_at: 2026-06-27T11:03:01.999Z
project: agent-context
topic: write-start-bootstrap-flow
source: agent
status: active
---
# Session Note

## Summary

Aligned the repository bootstrap flow with bounded project-memory startup so new work begins from `read_cold_start` and planning reads instead of `search_documents` or target-repository sidecar files.

## Actions

- Updated the `project-memory` ai-inst module so bounded startup begins with `read_cold_start`, uses planning reads next, and treats `search_documents` as a non-default fallback.
- Updated `instructions.local.md`, `README.md`, and `RUNBOOKS/WORK_ITEM_ORCHESTRATION.md` to describe the bounded bootstrap flow and cited-path-first inspection rule.
- Rebuilt `CLAUDE.md` and verified the generated instructions now reflect the bounded startup policy and no longer present `search_documents` as the default first read.

## Follow-up

- Close or advance dependent backlog items that rely on the bootstrap flow once their own implementation slices are complete.
