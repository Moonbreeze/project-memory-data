---
date: 2026-04-20
recorded_at: 2026-04-20T13:06:28.594Z
project: agent-context
topic: platform-neutral-curation
registry_scope: platform-neutral
source: agent
status: active
---
# Canonical Doc

## Summary

The context-curator contract must remain portable across agent platforms such as Claude, Codex, and Cursor, so the model is defined by inputs and outputs rather than vendor-specific workflow features.

## Guidance

- The curation model should be expressed as a platform-neutral contract that can be implemented on Claude, Codex, Cursor, or similar agent environments.
- Required inputs should stay minimal and portable: task statement, optional starting files, optional affected area, and access to the sidecar agent-context materials.
- Expected outputs should also stay portable: a short routing summary with start files, adjacent inspection targets, pitfalls, and verification hints.
- Vendor-specific orchestration features such as subagents, MCP wiring, or tool invocation style should be treated as adapters around the same logical contract rather than the contract itself.
- Documentation and procedures should avoid assuming one mandatory platform so the same knowledge layer remains reusable across teams and tools.

## References

- canonical-doc:agent-context:2026-04-20:context-curator-model
- canonical-doc:agent-context:2026-04-20:trial-mode
- runbook:agent-context:2026-04-20:request-curated-context
- decision:agent-context:2026-04-20:context-curator-platform-neutral
