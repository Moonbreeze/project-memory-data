---
date: 2026-03-15
project: project-memory
topic: work-item-planning-model
registry_scope: work-item-planning
source: agent
status: active
---
# Canonical Doc

## Summary

Work items are the executable planning surface of Project Memory: they model bounded implementation slices with explicit provenance, dependency edges, context and evidence references, and a planning state derived from lifecycle plus dependency resolution.

## Guidance

- Use work items for executable backlog slices, not for long-lived rationale or current truth; decisions, canonical docs, and runbooks remain separate roles.
- Keep origin, dependencies, context, verification, and evidence explicit in the work-item document instead of relying on dates, prose ordering, or hidden agent context.
- Represent independent branches as separate work items that may share the same origin decision or note without creating artificial dependency edges between them.
- Treat dependency metadata as planning input: ready, blocked, and in-progress behavior must derive from the actual work-item graph and lifecycle state rather than from document chronology alone.
- Use planning-backlog and planning-topic-entry as the primary read surfaces for work-item planning, and expand only from the candidate slice whose linked decisions, docs, or evidence are needed next.
- Keep work-item relationships same-project in the default model; cross-project planning helpers, if added later, must remain explicit opt-in surfaces rather than widening current planning behavior.

## References

- decision: work-item-dependency-model
- decision: work-item-origins-and-provenance
- decision: work-item-schema-and-lifecycle-model
- decision: work-item-backlog-fallback-policy
- decision: cross-project-helper-guardrails
