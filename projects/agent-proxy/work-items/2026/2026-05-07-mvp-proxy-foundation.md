---
date: 2026-05-07
recorded_at: 2026-05-07T10:38:44.761Z
project: agent-proxy
topic: mvp-proxy-foundation
source: agent
status: active
work_item_state: open
---
# Work Item

## Summary

Define and build the first MVP slice of agent-proxy around an OSS proxy base, safe input compression, and selective final-text expansion.

## Outcome

A concrete MVP design and implementation plan exists for a proxy that safely integrates transport compatibility, input compression, and optional output-side expansion without breaking tool use.

## Provenance

- ad-hoc: Initial project framing captured from the current discussion about a compression-aware proxy for coding agents.

## Dependencies

- none

## Context

- canonical-doc:agent-proxy:project-vision:project-vision
- canonical-doc:agent-proxy:architecture-direction:architecture-direction
- canonical-doc:agent-proxy:mvp-scope:mvp-scope
- decision:agent-proxy:2026-05-07:thin-custom-proxy-on-oss

## Verification

- Confirm the chosen proxy base can preserve streaming and tool-use semantics required by target CLIs.
- Define the v1 transform matrix covering passthrough, deterministic compression, reversible references, and optional cheap-model expansion by content type.
- Estimate expected token, latency, and reliability tradeoffs for the MVP flow.

## Evidence

- session-note:agent-proxy:2026-05-07:initial-project-framing
