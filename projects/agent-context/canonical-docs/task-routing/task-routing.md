---
date: 2026-06-21
recorded_at: 2026-06-21T12:01:42.841Z
project: agent-context
topic: task-routing
registry_scope: task-routing
source: agent
status: active
---
# Canonical Doc

## Summary

Task routing is a runtime harness behavior that selects the next bounded project-memory read and the first code paths to inspect for a concrete change.

## Guidance

- A stable architecture map alone is not enough; the harness also needs a routing layer that decides which bounded project-memory entrypoint to read next for a given task.
- Reusable routing patterns may be authored in agent-context, but project-specific routes and current truth should live in project-memory.
- The preferred startup flow for a target repository is to read cold-start context, open one relevant planning or topic package, and inspect only the cited code paths before widening the search.
- Useful routing outputs stay task-oriented: what to read first, what to inspect next, what pitfalls to avoid, and what to verify after the change.
- Repo-local ENTRYPOINTS or recipes in agent-context should be treated as authoring patterns or extraction sources, not as universal runtime storage for all projects.

## References

- canonical-doc:agent-context:2026-06-21:agent-context-overview
- canonical-doc:agent-context:2026-06-21:documentation-model
- runbook:agent-context:2026-06-21:bootstrap-task-context
- decision:agent-context:2026-06-21:authoring-repo-project-memory-split
