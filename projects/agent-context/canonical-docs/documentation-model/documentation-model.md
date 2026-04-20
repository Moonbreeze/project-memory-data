---
date: 2026-04-20
recorded_at: 2026-04-20T12:57:37.938Z
project: agent-context
topic: documentation-model
registry_scope: documentation-model
source: agent
status: active
---
# Canonical Doc

## Summary

The documentation model keeps only the lightweight artifacts needed for bounded agent bootstrap and excludes tracker-owned planning/history layers.

## Guidance

- The documentation set should prioritize bounded entry points over broad prose or encyclopedic architecture writeups.
- Needed document types are a start document, system map, constraints, area documents, decisions, runbooks, glossary, and task-routing artifacts such as entrypoints and recipes.
- Backlog, work-item tracking, and session notes are not part of the core model because task planning already exists in an external tracker.
- Documents should be short, path-aware, and written so an agent can trust their scope and intended use.
- Current truth, durable reasoning, and repeatable procedures should remain separated rather than mixed in one file.

## References

- canonical-doc:agent-context:2026-04-20:agent-context-overview
- canonical-doc:agent-context:2026-04-20:task-routing
- canonical-doc:agent-context:2026-04-20:trial-mode
- runbook:agent-context:2026-04-20:bootstrap-task-context
