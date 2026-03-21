---
date: 2026-03-21
recorded_at: 2026-03-21T00:00:00.000Z
project: project-memory
topic: fix-upsert-work-item-repair-flow-for-invalid-done-items
source: agent
status: active
work_item_state: done
---
# Work Item

## Summary

Fix the upsert_work_item repair flow so an existing invalid done work-item can be corrected by supplying new evidence or a non-terminal workItemState.

## Outcome

Project-memory can repair an already-invalid done work-item through upsert_work_item without requiring the stored document to already satisfy the done-state session-note evidence invariant before the new input is applied.

## Provenance

- ad-hoc: Implementation slice for Bug #2 in tests/KNOWN_BUGS.md: an existing invalid done work-item cannot be repaired through upsert_work_item because the write path reads and validates the stored document while resolving recorded_at before the new evidence or workItemState is applied.

## Dependencies

- none

## Context

- none

## Verification

- Verify upsertWorkItem can rewrite an existing invalid done work-item when the new input adds a valid session-note evidence locator.
- Verify upsertWorkItem can rewrite an existing invalid done work-item when the new input changes workItemState away from done.
- Verify recorded_at preservation on rewrite does not require strict readDocument validation of the stored work-item body before the repair input is applied.
- Add regression coverage for both core and MCP repair paths with Bug #2 comments in the covering tests.

## Evidence

- session-note:project-memory:2026-03-21:fix-upsert-work-item-repair-flow-for-invalid-done-items
- verification-result:project-memory:2026-03-21:fix-upsert-work-item-repair-flow-for-invalid-done-items
