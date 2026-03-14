---
date: 2026-03-14
project: project-memory
topic: work-item-backlog-fallback-policy
source: agent
status: active
---
# Decision

## Context

Session 6 introduces the first live work-item document type and a project-scoped backlog planning view, but existing projects and cross-project queries still rely on the older decision-backed backlog behavior. Switching every backlog query to work items immediately would break compatibility for projects that have not created work-item documents yet and would overreach on cross-project dependency interpretation.

## Decision

Use project-scoped work-item backlog planning only when the caller requests the `backlog` preset for a specific project that already has managed work-item documents. In every other case, keep the bounded fallback to the legacy decision backlog view.

## Consequences

- Projects can adopt work-item planning incrementally without losing backlog visibility before their first work-item records exist.
- Project-scoped backlog queries can derive ready, in-progress, and blocked work from dependency metadata without forcing cross-project dependency reasoning.
- Unscoped or pre-migration backlog reads remain compatible with the existing decision-backed surface until a later migration phase replaces that fallback.
