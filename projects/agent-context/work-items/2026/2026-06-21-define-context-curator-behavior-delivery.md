---
date: 2026-06-21
recorded_at: 2026-06-21T19:13:50.167Z
project: agent-context
topic: define-context-curator-behavior-delivery
source: agent
status: active
work_item_state: done
---
# Work Item

## Summary

Define how context-curator and delegation-policy behavior is authored in agent-context and delivered through ai-inst/opencode without target-repository scaffold files.

## Outcome

A delivery model exists for Claude, Codex, and Cursor bindings that reuses shared authoring sources, carries orchestrator-first delegation guidance through behavior-layer delivery, and does not copy harness artifacts into target repositories.

## Provenance

- ad-hoc: Follow-up after rejecting target-repository scaffold delivery in favor of behavior-layer delivery through ai-inst/opencode.

## Dependencies

- work-item:agent-context:2026-04-20:define-context-curator-contract

## Context

- canonical-doc:agent-context:2026-06-21:context-curator-model
- canonical-doc:agent-context:2026-06-21:platform-neutral-curation
- decision:agent-context:2026-06-21:authoring-repo-project-memory-split
- decision:agent-context:2026-06-21:no-target-repo-harness-traces
- decision:agent-context:2026-06-22:orchestrator-first-delegation

## Verification

- One shared authoring source exists for the curator contract.
- Platform bindings are defined as behavior-layer integrations, not target-repo scaffold output.
- The delivery path goes through ai-inst/opencode or equivalent runtime surfaces.
- Orchestrator-first delegation guidance is extracted from local authoring sources into behavior-layer delivery surfaces.
- The delivered policy preserves minimal delegated handoff and path-not-content guidance where the runtime supports it.
- No repo-local harness artifacts are required in target repositories.
- Remaining integration steps are documented for behavior-layer setup only.

## Evidence

- session-note:agent-context:2026-06-27:define-context-curator-behavior-delivery
- verification-result:agent-context:2026-06-27:define-context-curator-behavior-delivery
