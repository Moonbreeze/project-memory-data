---
date: 2026-03-14
project: claude-remote
topic: runtime-name
source: agent
status: draft
---
# Decision

## Context

The repository has evolved from a Claude-specific remote tool into a provider-neutral runtime with session management, transport layers, and emerging agent-orchestration concerns such as session handoff. The current technical repository name, `claude-remote`, is historically accurate but increasingly narrower than the intended product/runtime scope. A future-facing name is useful for documentation and product terminology, but a full repository/package rename would introduce unnecessary churn before the public terminology and UX stabilize.

## Decision

Treat `Waypoint` as the preferred future product/runtime name for the provider-neutral orchestration system, while keeping `claude-remote` as the current repository and package identifier until a separate rename decision is made.

## Consequences

- Documentation may refer to `Waypoint` as a future-facing runtime or product name without implying that the repository, package name, or imports have already changed.
- Future sessions should evaluate naming changes against this draft instead of restarting the naming discussion from scratch.
- A separate follow-up decision is still required before renaming the repository, package metadata, public API terminology, or import paths.
