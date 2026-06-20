---
date: 2026-06-20
recorded_at: 2026-06-20T15:09:45.234Z
project: agent-harness
topic: harness-architecture
registry_scope: architecture
source: agent
status: active
---
# Canonical Doc

## Summary

System boundary and source-of-truth model for the agent-harness meta-project.

## Guidance

- agent-harness is a separate meta-project for designing and evolving the agent runtime, workflow, and user interaction model.
- project-memory is the canonical specification and rationale surface for agent-harness.
- The agent-harness repository stores executable runtime artifacts such as agent definitions, prompts, command shortcuts, scenarios, and examples.
- ai-inst stores reusable instruction modules and reusable skills that can be shared across projects.
- Global opencode configuration is a local wiring surface for providers, model selection, and agent activation, not the canonical specification surface.
- Canonical architecture and workflow guidance must not be duplicated as repository docs when project-memory already owns that authority.

## References

- decision:agent-harness:2026-06-20:separate-agent-harness-project
- decision:agent-harness:2026-06-20:project-memory-as-canonical-spec
