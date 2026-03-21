---
date: 2026-03-21
recorded_at: 2026-03-21T00:00:00.000Z
project: project-memory
topic: fix-upsert-work-item-repair-flow-for-invalid-done-items
source: agent
status: active
---
# Session Note

## Summary

Implemented the repair-path fix for invalid done work-items so upsert_work_item can preserve recorded_at without requiring the previously stored document to already pass strict work-item validation.

## Actions

- Refactored document storage reads so frontmatter-only metadata can be reused during rewrite flows without invoking strict stored work-item validation.
- Updated recorded_at write resolution to preserve the existing timeline key from validated frontmatter when rewriting an existing managed document.
- Added regression coverage for repairing invalid done work-items through both the core upsertWorkItem path and the MCP upsert_work_item tool, including evidence-repair and state-change repair cases.
- Updated tests/KNOWN_BUGS.md to mark Bug #2 fixed with covering test references.

## Follow-up

- No immediate follow-up is required for this slice unless a later cleanup chooses to archive the completed work-item.
