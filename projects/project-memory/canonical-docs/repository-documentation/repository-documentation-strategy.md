---
date: 2026-03-21
recorded_at: 2026-03-21T00:00:00.000Z
project: project-memory
topic: repository-documentation-strategy
registry_scope: repository-documentation
source: user
status: active
---
# Canonical Doc

## Summary

The tool-repository docs should be organized by audience, with shared core concepts stated once and each document carrying a distinct explanatory job.

## Guidance

- Keep README as the new-user entrypoint: define core concepts once, show the onboarding path, and describe only current supported surfaces and requirements.
- Keep docs/usage.md as the practical workflow guide: explain document responsibilities, lifecycle patterns, migration guidance, and bounded-read usage in the system's own terms rather than as a command catalog.
- Keep docs/architecture.md as the contributor-facing system model: focus on repository boundaries, core layering, retrieval behavior, path and document contracts, and implementation constraints.
- State repo split, MCP-first workflow, and the CLI's secondary role once in README; in other docs, refer back to those concepts only when a local section cannot stand without them.
- Treat repeated restatement of the same core product thesis across README, usage, and architecture as a documentation-structure smell.
- Use examples and diagrams only when they make the document model or workflow materially easier to understand; remove them when they merely repeat surrounding prose.
- Do not mix roadmap hints or speculative future UX into onboarding copy; future-facing ideas belong in decisions, work-items, or backlog documents instead of README guidance.

## References

- decision:repository-documentation-information-architecture
- canonical-doc:system-overview
