---
date: 2026-04-20
recorded_at: 2026-04-20T12:57:44.484Z
project: agent-context
topic: task-routing
registry_scope: task-routing
source: agent
status: active
---
# Canonical Doc

## Summary

Task routing is the primary mechanism for the common scenario where an agent needs to know where to start and which files to inspect for a concrete change.

## Guidance

- A stable architecture map is not enough for common change requests; the project also needs a routing layer that answers where to start for a task type.
- The routing layer should be expressed in task terms such as change type, start here, usually also inspect, pitfalls, and verify with.
- Useful routing artifacts include ENTRYPOINTS indexes, change recipes, hotspot notes, and file-pattern guidance.
- The preferred startup flow is to read the start document, open one routing document, and inspect only the cited code paths before widening the search.
- This routing layer should be optimized for the scenario 'make this change and start from these files'.

## References

- canonical-doc:agent-context:2026-04-20:agent-context-overview
- canonical-doc:agent-context:2026-04-20:documentation-model
- runbook:agent-context:2026-04-20:bootstrap-task-context
- decision:agent-context:2026-04-20:agent-context-sidecar-trial
