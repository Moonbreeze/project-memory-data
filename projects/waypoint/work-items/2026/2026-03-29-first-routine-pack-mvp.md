---
date: 2026-03-29
recorded_at: 2026-03-29T10:38:45.183Z
project: waypoint
topic: first-routine-pack-mvp
source: agent
status: active
work_item_state: open
---
# Work Item

## Summary

Author the first routine-pack manifest that matches the user's real project workflow from idea clarification through implementation, verification, review, and follow-up triage.

## Outcome

Waypoint has a first concrete routine pack describing the user's habitual delivery flow for new projects and follow-up changes: clarify the idea, shape scope and resources, author or update foundation documentation, plan MVP work items, implement one work item per session, verify or review the slice, and triage follow-up UX or backlog items. The pack becomes the first reusable example of how routine orchestration should feel in practice.

## Provenance

- decision:waypoint:2026-03-29:routine-pack-orchestration

## Dependencies

- work-item:waypoint:2026-03-29:routine-pack-domain-model-mvp

## Context

- session-note:waypoint:2026-03-29:routine-pack-architecture-exploration
- decision:waypoint:2026-03-29:routine-pack-orchestration

## Verification

- The pack defines entrypoints and routines for idea clarification, scope shaping, documentation/backlog preparation, single-work-item execution, verification, review, and follow-up triage.
- The pack defines workload classes and pack-level model routing without hardcoding concrete models directly into routine definitions.
- Routines specify selective ai-inst instruction loadouts rather than blindly loading all project instructions.
- Durable outputs expected from documentation, verification, or review-related routines are modeled so they can flow into project-memory instead of a parallel documentation store.

## Evidence

- none
