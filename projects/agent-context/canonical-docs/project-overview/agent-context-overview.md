---
date: 2026-04-20
recorded_at: 2026-04-20T12:57:31.773Z
project: agent-context
topic: agent-context-overview
registry_scope: project-overview
source: agent
status: active
---
# Canonical Doc

## Summary

Agent-context is a sidecar knowledge layer that reduces startup context cost for AI agents working on a large frontend project.

## Guidance

- The project exists to reduce unnecessary context usage at task startup rather than to document the entire codebase.
- The preferred outcome is a cheap bootstrap flow: read a small entry layer, choose one relevant routing document, and inspect only the needed code paths.
- The knowledge base is intended to live alongside a primary product repository as a sidecar project, not as a mandatory in-repo documentation layer during the trial phase.
- The initial target users are AI agents and engineers using agents for frontend maintenance tasks.
- The project should optimize for fast task entry, not for exhaustive historical coverage.

## References

- canonical-doc:agent-context:2026-04-20:documentation-model
- canonical-doc:agent-context:2026-04-20:task-routing
- canonical-doc:agent-context:2026-04-20:trial-mode
- decision:agent-context:2026-04-20:agent-context-sidecar-trial
