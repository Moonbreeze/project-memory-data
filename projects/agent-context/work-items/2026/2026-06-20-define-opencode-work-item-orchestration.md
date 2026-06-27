---
date: 2026-06-20
recorded_at: 2026-06-20T18:35:50.480Z
project: agent-context
topic: define-opencode-work-item-orchestration
source: agent
status: active
work_item_state: done
---
# Work Item

## Summary

Define how the opencode harness uses ai-inst behavior and project-memory for fresh work-item startup, same-context overrides, and orchestrator-first delegation policy.

## Outcome

An explicit opencode orchestration policy exists for fresh work-item startup, bounded reads, handoff between work-items, allowed same-context overrides, subagent delegation thresholds, and minimal handoff/tool-partition rules.

## Provenance

- ad-hoc: Follow-up after establishing the default new-session policy for work-item transitions and evaluating how to realize it in opencode.

## Dependencies

- work-item:agent-context:2026-04-20:define-context-curator-contract

## Context

- canonical-doc:agent-context:2026-06-21:context-curator-model
- canonical-doc:agent-context:2026-06-21:platform-neutral-curation
- decision:agent-context:2026-06-21:authoring-repo-project-memory-split
- decision:agent-context:2026-06-22:orchestrator-first-delegation

## Verification

- Define the bounded project-memory input context that a fresh Task should receive for a new work-item.
- Define the default policy 'new work-item -> new Task or subagent'.
- Define the allowed override cases for continuing in the same context.
- Define the handoff contract between a completed work-item and the next work-item.
- Define when the orchestrator should execute directly instead of spawning a subagent.
- Define when spawning a subagent is justified in opencode.
- Define the default read-only subagent profile and primary-only heavy tool guidance.
- Define the default path-not-content handoff rule for delegated helpers.
- Ensure the policy can connect to future platform adapters without hard-coding one vendor workflow.
- Startup does not require creating repo-local harness files in the target repository.

## Evidence

- session-note:agent-context:2026-06-27:define-opencode-work-item-orchestration
- verification-result:agent-context:2026-06-27:define-opencode-work-item-orchestration
