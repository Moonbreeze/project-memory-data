---
date: 2026-05-07
recorded_at: 2026-05-07T10:38:37.623Z
project: agent-proxy
topic: thin-custom-proxy-on-oss
source: agent
status: active
---
# Decision

## Context

The project goal is to reduce token cost for coding agents without breaking streaming, tool use, or structured outputs. Existing open-source projects already cover major parts of the problem space: transport-compatible proxies, deterministic input compression, deduplication, noise stripping, and reversible retrieval. What is missing is a coherent product layer that applies these ideas safely across coding-agent traffic and adds output-side token reduction for plain natural-language responses.

## Decision

Build agent-proxy as a thin custom compression and policy layer on top of an existing open-source proxy transport, reusing proven input-compression patterns and adding selective output-side compacting and expansion only where protocol-safe.

## Consequences

- The project can move faster by avoiding a greenfield proxy transport implementation.
- Input-side savings can be delivered early by borrowing established compression patterns before inventing novel codecs.
- The main differentiated work becomes policy, segmentation, safety rules, measurement, and output-side expansion.
- A universal intermediate language is explicitly deprioritized in favor of typed or content-specific representations where useful.
- The architecture depends on carefully defined bypass and fallback behavior to avoid protocol corruption.

## Stable Guidance Review

- Outcome: updated
- Summary: Reviewed current stable guidance and updated the stable guidance in the same change slice.
