---
date: 2026-06-21
recorded_at: 2026-06-21T12:01:42.855Z
project: agent-context
topic: context-curator-model
registry_scope: context-curator
source: agent
status: active
---
# Canonical Doc

## Summary

Context-curator is a narrow helper role that reads bounded project context, usually from project-memory, and returns a compressed routing handoff for a concrete task.

## Guidance

- Context-curator is responsible for finding the smallest relevant context slice for a concrete change request and compressing it into a short handoff.
- The preferred output shape remains task-oriented: Start here, Also inspect, Pitfalls, Verify, and optionally Update docs when a reusable authoring pattern should change.
- For target-project work, the curator should treat project-memory as the primary source of project-specific truth rather than treating agent-context as a sidecar knowledge base for that repository.
- Authoring materials in agent-context may still inform the curator's reusable routing patterns, templates, or output expectations.
- Context-curator is not responsible for solving the full task, performing broad repository exploration by default, or becoming the default reader of all project knowledge.

## References

- canonical-doc:agent-context:2026-06-21:task-routing
- canonical-doc:agent-context:2026-06-21:platform-neutral-curation
- runbook:agent-context:2026-06-21:request-curated-context
- decision:agent-context:2026-06-21:authoring-repo-project-memory-split
