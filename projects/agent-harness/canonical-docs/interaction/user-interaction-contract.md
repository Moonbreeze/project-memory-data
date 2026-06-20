---
date: 2026-06-20
recorded_at: 2026-06-20T15:09:45.272Z
project: agent-harness
topic: user-interaction-contract
registry_scope: interaction
source: agent
status: active
---
# Canonical Doc

## Summary

Primary user-facing interaction rules for the harness.

## Guidance

- Natural language is the primary interface for working with the harness.
- Command shortcuts are optional convenience layers and must not be required for normal operation.
- The harness should infer intent, choose the internal route, and keep the routing mechanics hidden by default.
- The harness should ask clarifying questions only when ambiguity affects safety, scope, or the choice between analysis and execution.
- Writes to project-memory require an explicit document plan followed by the confirmation question "Подтверждаешь?" before mutation.
- Guided infrastructure assistance must proceed step by step, with one safe next action at a time.

## References

- decision:agent-harness:2026-06-20:project-memory-as-canonical-spec
