---
date: 2026-04-20
recorded_at: 2026-04-20T12:57:52.394Z
project: agent-context
topic: trial-mode
registry_scope: trial-mode
source: agent
status: active
---
# Canonical Doc

## Summary

The initial operating mode is a sidecar trial: documentation may live near the target repository, be owned by one person at first, and must expose its authority level clearly.

## Guidance

- The documentation may live outside the main product repository during the initial trial period as a sidecar project.
- Trial documents must expose their maturity and authority so agents do not mistake exploratory notes for canonical truth.
- A single start document should declare that the documentation is in trial mode, where it lives, and which documents should be read first.
- The trial should optimize for proving reduced startup context cost on real tasks before introducing heavier infrastructure such as MCP-backed query surfaces.
- A thin bridge from the main repository to the sidecar docs is useful so agents can reliably discover the sidecar context.

## References

- canonical-doc:agent-context:2026-04-20:agent-context-overview
- canonical-doc:agent-context:2026-04-20:documentation-model
- decision:agent-context:2026-04-20:agent-context-sidecar-trial
