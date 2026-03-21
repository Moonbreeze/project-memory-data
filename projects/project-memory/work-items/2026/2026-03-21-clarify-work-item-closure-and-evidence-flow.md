---
date: 2026-03-21
recorded_at: 2026-03-21T00:00:00.000Z
project: project-memory
topic: clarify-work-item-closure-and-evidence-flow
source: agent
status: archived
work_item_state: done
---
# Work Item

## Summary

Clarify and implement the authoritative work-item closure flow so agents treat session-note evidence, verification guidance, and close-work-item semantics consistently.

## Outcome

Project-memory has an explicit implementation slice for making the work-item closure flow unambiguous in tool guidance and code, including a hard done-state evidence invariant and clearer MCP recommendations, with public documentation updates tracked as part of the slice because work-item lifecycle is a flagship user-facing flow.

## Provenance

- ad-hoc: Follow-up from agent workflow review: the close-work-item flow and evidence update expectations are currently implicit enough that other agents can misread or skip them.

## Dependencies

- none

## Context

- none

## Verification

- Verify the done-state write path rejects work items that lack at least one session-note locator in evidence.
- Verify MCP tool descriptions and choose_workflow guidance explicitly distinguish evidence updates from close_work_item and require verification-result guidance for code-work slices.
- Verify the public repository documentation reflects the clarified work-item lifecycle so a new user can understand the expected closure flow without inferring it from tests or source.
- Verify existing close/archive behavior remains intact for valid terminal work items after the invariant and guidance changes.

## Evidence

- session-note:project-memory:2026-03-21:clarify-work-item-closure-and-evidence-flow
- verification-result:project-memory:2026-03-21:clarify-work-item-closure-and-evidence-flow
