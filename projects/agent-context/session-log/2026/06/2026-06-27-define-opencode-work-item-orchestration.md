---
date: 2026-06-27
recorded_at: 2026-06-27T10:17:06.042Z
project: agent-context
topic: define-opencode-work-item-orchestration
source: agent
status: active
---
# Session Note

## Summary

Refined the opencode work-item orchestration policy in authoring docs and runtime instructions, including bounded startup order, minimal helper handoff, and primary-orchestrator-only heavy actions.

## Actions

- Updated instructions.local.md to define the bounded startup read order for a newly selected work-item.
- Updated instructions.local.md to define the default helper package with project slug and work-item planning handle.
- Updated instructions.local.md to keep project-memory writes, ai-inst builds/rule changes, git history changes, and final cross-cutting verification in the primary orchestrator.
- Updated RUNBOOKS/WORK_ITEM_ORCHESTRATION.md with a default read-only helper profile and clarified minimal delegated handoff boundaries.
- Rebuilt CLAUDE.md through ai-inst so the runtime instructions reflect the new orchestration policy.

## Follow-up

- Use the finalized policy as the dependency baseline before implementing opencode work-item orchestration runtime behavior.
