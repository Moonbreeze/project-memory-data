---
date: 2026-06-21
recorded_at: 2026-06-21T12:01:42.784Z
project: agent-context
topic: trial-mode
registry_scope: trial-mode
source: agent
status: active
---
# Canonical Doc

## Summary

The current trial validates the authoring-to-runtime pipeline: author workflow guidance in agent-context, deliver behavior via ai-inst/opencode, and bootstrap target-project work from project-memory.

## Guidance

- The trial is no longer defined as keeping a sidecar runtime knowledge base near each target repository.
- Trial work should focus on proving that authoring materials in agent-context can become effective ai-inst modules, skills, and harness instructions.
- Project-specific context for real tasks should be read from project-memory using bounded entrypoints rather than from repo-local START or ENTRYPOINTS files in unrelated repositories.
- Trial materials must still expose maturity and authority clearly so exploratory authoring notes are not mistaken for stable runtime policy.
- A useful trial outcome is a minimal end-to-end flow that connects authoring docs, generated behavior artifacts, and project-memory-backed execution on real tasks.

## References

- canonical-doc:agent-context:2026-06-21:agent-context-overview
- canonical-doc:agent-context:2026-06-21:documentation-model
- decision:agent-context:2026-06-21:authoring-repo-project-memory-split
- decision:agent-context:2026-04-20:agent-context-sidecar-trial
