---
date: 2026-06-21
recorded_at: 2026-06-21T12:01:42.698Z
project: agent-context
topic: documentation-model
registry_scope: documentation-model
source: agent
status: active
---
# Canonical Doc

## Summary

The documentation model separates authoring documents in agent-context, runtime behavior delivered by ai-inst/opencode, and project-specific records stored in project-memory.

## Guidance

- Agent-context stores authoring documents, design notes, patterns, and source materials that may later be extracted into ai-inst modules or skills.
- Opencode configuration plus ai-inst modules and skills define the runtime behavior of the harness, including startup flow, routing behavior, and memory-write policy.
- Project-memory stores project-specific current truth, planning state, decisions, runbooks, verification results, and execution evidence for a target repository.
- Repository-local Markdown in agent-context should not be treated as the primary canonical knowledge layer for unrelated projects.
- Documents should stay explicit about which layer they belong to: authoring repo, behavior layer, or project-memory data layer.
- Current truth, durable rationale, repeatable procedure, and execution history should remain separated in project-memory rather than collapsed into generic sidecar prose.
- Target repositories should not become a durable storage surface for harness-specific artifacts by default.
- Harness behavior should be delivered through behavior-layer tooling such as ai-inst/opencode rather than through repo-local scaffold files in target repositories.
- Temporary runtime artifacts needed only during execution should stay outside the target repository or be removed instead of becoming a durable knowledge layer.

## References

- canonical-doc:agent-context:2026-06-21:agent-context-overview
- canonical-doc:agent-context:2026-06-21:task-routing
- canonical-doc:agent-context:2026-06-21:trial-mode
- decision:agent-context:2026-06-21:authoring-repo-project-memory-split
- decision:agent-context:2026-06-21:no-target-repo-harness-traces
