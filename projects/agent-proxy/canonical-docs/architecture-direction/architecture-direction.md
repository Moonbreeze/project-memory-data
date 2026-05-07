---
date: 2026-05-07
recorded_at: 2026-05-07T10:38:31.217Z
project: agent-proxy
topic: architecture-direction
registry_scope: architecture-direction
source: agent
status: active
---
# Canonical Doc

## Summary

The preferred architecture is a thin custom compression proxy built on top of an existing OSS proxy transport and existing compression ideas, with selective output-side expansion as a differentiator.

## Guidance

- Reuse an existing proxy transport for API compatibility, streaming, authentication, and tool-use mediation instead of rebuilding transport from scratch.
- Implement a custom policy layer that classifies content segments and decides between passthrough, deterministic compression, ML-assisted compression, reversible references, and cheap-model expansion.
- Focus input compression on the highest-yield categories: long history, repeated file content, logs, diffs, test output, and other noisy tool payloads.
- Restrict output-side compression and re-expansion to plain assistant prose; bypass tool calls, JSON, XML envelopes, patch blocks, and machine-sensitive code payloads.
- Use typed intermediate representations only where they improve safety or reversibility; a single shared language for all input and output is not required.
- Design every transform with fallbacks so low-confidence or protocol-sensitive cases degrade to passthrough instead of corruption.

## References

- canonical-doc:agent-proxy:2026-05-07:project-vision
- decision:agent-proxy:2026-05-07:thin-custom-proxy-on-oss
- work-item:agent-proxy:2026-05-07:mvp-proxy-foundation
