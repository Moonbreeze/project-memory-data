---
date: 2026-05-07
recorded_at: 2026-05-07T10:38:24.561Z
project: agent-proxy
topic: project-vision
registry_scope: project-vision
source: agent
status: active
---
# Canonical Doc

## Summary

Agent-proxy is a compression-aware LLM proxy for coding agents that optimizes token spend without breaking tool use, streaming, or structured outputs.

## Guidance

- Prioritize token savings where coding agents actually spend tokens: system prompts, chat history, file reads, diffs, logs, and test output.
- Treat compression as content-aware transformation rather than a single universal intermediate language.
- Keep protocol safety as a first-class requirement: tool calls, structured outputs, patches, and code-oriented payloads must bypass unsafe transforms.
- Measure success by end-to-end economics and reliability: input tokens, output tokens, latency, failure rate, and semantic regressions.
- Prefer reversible or recoverable compression for high-risk inputs so the original content can be retrieved when needed.

## References

- canonical-doc:agent-proxy:2026-05-07:architecture-direction
- decision:agent-proxy:2026-05-07:thin-custom-proxy-on-oss
- work-item:agent-proxy:2026-05-07:mvp-proxy-foundation
