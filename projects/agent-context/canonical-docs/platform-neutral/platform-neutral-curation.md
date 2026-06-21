---
date: 2026-06-21
recorded_at: 2026-06-21T12:01:42.867Z
project: agent-context
topic: platform-neutral-curation
registry_scope: platform-neutral
source: agent
status: active
---
# Canonical Doc

## Summary

Platform-neutral curation defines a portable contract for producing bounded routing guidance from project context without coupling the model to one vendor runtime.

## Guidance

- The curation model should be expressed as a platform-neutral contract that can be implemented on Claude, Codex, Cursor, or similar agent environments.
- Required inputs should stay minimal and portable: task statement, project identifier or equivalent context handle, optional starting files, and optional affected area.
- The preferred project-specific data source is bounded project context from project-memory, though platform adapters may obtain the same logical inputs through different integration surfaces.
- Expected outputs should stay portable: a short routing summary with start files or documents, adjacent inspection targets, pitfalls, and verification hints.
- Vendor-specific orchestration features such as subagents, MCP wiring, or tool invocation style should be treated as adapters around the same logical contract rather than the contract itself.

## References

- canonical-doc:agent-context:2026-06-21:context-curator-model
- canonical-doc:agent-context:2026-06-21:trial-mode
- runbook:agent-context:2026-06-21:request-curated-context
- decision:agent-context:2026-06-21:authoring-repo-project-memory-split
