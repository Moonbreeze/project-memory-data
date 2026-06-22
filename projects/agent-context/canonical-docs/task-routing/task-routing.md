---
date: 2026-06-22
recorded_at: 2026-06-22T13:39:59.044Z
project: agent-context
topic: task-routing
registry_scope: task-routing
source: agent
status: active
---
# Canonical Doc

## Summary

Task routing chooses the next bounded project-memory read and the first execution path for a concrete change, which may end in either local orchestrator execution or a minimal delegated helper flow.

## Guidance

- A stable architecture map alone is not enough; the harness also needs a routing layer that decides which bounded project-memory entrypoint to read next for a given task.
- Reusable routing patterns may be authored in agent-context, but project-specific routes and current truth should live in project-memory.
- The preferred startup flow for a target repository is to read cold-start context, open one relevant planning or topic package, and inspect only the cited code paths before widening the search.
- Useful routing outputs stay task-oriented: what to read first, what to inspect next, what pitfalls to avoid, and what to verify after the change.
- Routing does not need to delegate by default; local orchestrator execution is a valid next step when the task is small, local, and cheaper than spawning a helper.
- When delegation is chosen, the handoff should stay minimal: task, success criteria, starting paths, explicit constraints, and expected result shape.
- When code context must be pointed out to a delegated helper, prefer source paths and line ranges over passing full file contents unless the text is external to the workspace or otherwise cannot be reread locally.
- Repo-local ENTRYPOINTS or recipes in agent-context should be treated as authoring patterns or extraction sources, not as universal runtime storage for all projects.

## References

- canonical-doc:agent-context:2026-06-21:agent-context-overview
- canonical-doc:agent-context:2026-06-21:documentation-model
- runbook:agent-context:2026-06-21:bootstrap-task-context
- decision:agent-context:2026-06-21:authoring-repo-project-memory-split
- decision:agent-context:2026-06-22:orchestrator-first-delegation
- provider-note:agent-context:2026-06-22:opencode
