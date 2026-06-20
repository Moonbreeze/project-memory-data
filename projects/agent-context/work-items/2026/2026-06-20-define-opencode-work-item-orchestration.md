---
date: 2026-06-20
recorded_at: 2026-06-20T18:35:50.480Z
project: agent-context
topic: define-opencode-work-item-orchestration
source: agent
status: active
work_item_state: open
---
# Work Item

## Summary

Define how agent-context should be used in opencode to start a fresh Task or subagent for each new work-item by default.

## Outcome

An explicit orchestration policy exists for opencode that defines default fresh-context execution, handoff between work-items, and allowed override cases.

## Provenance

- ad-hoc: Follow-up after establishing the default new-session policy for work-item transitions and evaluating how to realize it in opencode.

## Dependencies

- work-item:agent-context:2026-04-20:define-context-curator-contract

## Context

- canonical-doc:agent-context:2026-04-20:context-curator-model
- canonical-doc:agent-context:2026-04-20:platform-neutral-curation
- decision:agent-context:2026-04-20:context-curator-platform-neutral

## Verification

- Define the bounded input context that a fresh Task should receive for a new work-item.
- Define the default policy 'new work-item -> new Task or subagent'.
- Define the allowed override cases for continuing in the same context.
- Define the handoff contract between a completed work-item and the next work-item.
- Ensure the policy can connect to future platform adapters without hard-coding one vendor workflow.

## Evidence

- none
