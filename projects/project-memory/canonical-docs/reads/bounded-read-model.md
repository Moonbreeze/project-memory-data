---
date: 2026-03-14
project: project-memory
topic: bounded-read-model
registry_scope: reads
source: agent
status: active
---
# Canonical Doc

## Summary

Bounded reads are the tool's narrow retrieval layer: they return deterministic, stage-explained document packages for common agent tasks instead of broad project scans or implicit graph traversal.

## Guidance

- Prefer bounded read entrypoints for startup, topic lookup, rationale lookup, and planning instead of scanning whole projects through generic list or search flows.
- Keep bounded read behavior deterministic through fixed per-stage limits, explicit stage ordering, status filters, and path dedupe.
- Use planning-backlog for project-scoped active work-item planning and planning-topic-entry for exact-topic planning context built from selected work items plus explicit same-project follows.
- Treat planning explainability as metadata about selected work items rather than as a reason to widen the returned document package implicitly.
- Keep cross-project material out of default bounded reads; any future cross-project helper must be explicit, opt-in, and separately bounded.

## References

- decision: work-item-backlog-fallback-policy
- decision: canonical-doc-minimal-shape
- decision: cross-project-helper-guardrails
- runbook: read-entrypoints-baseline
- runbook: work-planning-read-refinement
