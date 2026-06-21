---
date: 2026-06-21
recorded_at: 2026-06-21T12:40:04.275Z
project: agent-context
topic: implement-opencode-work-item-orchestration
source: agent
status: active
work_item_state: open
---
# Work Item

## Summary

Implement the opencode runtime flow for starting a new work-item with fresh bounded context and explicit handoff rules.

## Outcome

Opencode can start a new work-item from bounded project-memory reads by default, supports narrow same-context overrides, and preserves a short verified handoff contract between work-items.

## Provenance

- ad-hoc: Follow-up after defining the platform-neutral work-item orchestration policy for opencode.

## Dependencies

- work-item:agent-context:2026-06-20:define-opencode-work-item-orchestration

## Context

- canonical-doc:agent-context:2026-06-21:context-curator-model
- canonical-doc:agent-context:2026-06-21:platform-neutral-curation
- decision:agent-context:2026-06-21:authoring-repo-project-memory-split

## Verification

- Define where opencode detects the start of a new work-item.
- Define how opencode launches a fresh Task, subagent, or equivalent fresh context when available.
- Define the exact bounded project-memory reads used for new work-item startup.
- Define the explicit override path for continuing in the same context.
- Define the handoff payload passed from a completed work-item to the next one.
- Ensure the implementation surface stays adapter-friendly and does not hard-code one vendor-specific orchestration model beyond opencode runtime integration.
- Runtime implementation does not introduce repo-local harness prompts, bootstrap files, or metadata into target repositories by default.

## Evidence

- none
