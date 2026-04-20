---
date: 2026-04-20
recorded_at: 2026-04-20T13:06:21.719Z
project: agent-context
topic: context-curator-model
registry_scope: context-curator
source: agent
status: active
---
# Canonical Doc

## Summary

Context-curator is a narrow helper role that reads only the relevant agent-context materials, returns a compressed routing summary, and optionally updates durable routing artifacts after a task.

## Guidance

- Context-curator is responsible for finding the smallest relevant context slice for a concrete change request and compressing it into a short handoff.
- The preferred output shape is task-oriented: Start here, Also inspect, Pitfalls, Verify, and optionally Update docs if a stable new route was discovered.
- The role should read only the start document plus the smallest relevant routing or area documents before touching code paths named by those documents.
- Context-curator is not responsible for solving the full task, performing broad repository exploration, or becoming the default reader of all project knowledge.
- The role is most useful when the main task begins with uncertainty about where to start or when a new stable routing pattern should be captured after finishing a task.

## References

- canonical-doc:agent-context:2026-04-20:task-routing
- canonical-doc:agent-context:2026-04-20:platform-neutral-curation
- runbook:agent-context:2026-04-20:request-curated-context
- decision:agent-context:2026-04-20:context-curator-platform-neutral
