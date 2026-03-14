---
date: 2026-03-14
project: project-memory
topic: work-item-implementation-session-6
source: agent
status: active
---
# Session Note

## Summary

Implemented the first live work-item document type and the initial project-scoped backlog planning surface in the tool repo using the Session 5 spec as the contract.

## Actions

- Added managed `work-item` document support with deterministic paths, `work_item_state` frontmatter, body rendering/parsing, schema validation, and read/list/search compatibility.
- Added project-scoped backlog planning that switches to work items when they exist for the requested project, computes ready versus blocked from dependency state, and falls back to the legacy decision backlog otherwise.
- Added CLI `upsert-work-item`, MCP `upsert_work_item`, bootstrap/install support for work-item directories, and commit-scope support for `docs(<project>/work-item): ...`.
- Updated tool-repo documentation and kept bounded read entrypoints intentionally unchanged apart from clarifying that work-item sources remain out of scope there until dedicated planning reads are added.

## Follow-up

- Add a dedicated bounded planning read entrypoint that consumes work-item backlog state directly.
- Decide when projects should stop relying on the decision backlog fallback after work-item rollout stabilizes.
- Evaluate whether Session 7 should introduce a dedicated close/archive helper on top of the current upsert-based lifecycle updates.
