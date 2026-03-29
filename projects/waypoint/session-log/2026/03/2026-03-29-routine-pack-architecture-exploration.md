---
date: 2026-03-29
recorded_at: 2026-03-29T10:38:45.033Z
project: waypoint
topic: routine-pack-architecture-exploration
source: agent
status: active
---
# Session Note

## Summary

Explored how to add reusable routine-pack orchestration to Waypoint without duplicating ai-inst or project-memory. The discussion converged on a coordinator-plus-typed-routines model, clarified that provider `plan_updated` remains telemetry rather than reusable execution state, and established the initial architecture for routine packs, workload routing, instruction loadouts, built-in runtime primitives, and durable artifact handling.

## Actions

- Compared deterministic workflow orchestration against free-form goal-driven chat execution and concluded that a pure deterministic plan is a poor primary fit for user requests stated as goals rather than workflows.
- Adopted a hybrid model where an agent-coordinator interprets user goals but may invoke only registered typed routines instead of arbitrary improvised steps.
- Separated orchestration concerns from existing provider runtime concerns by treating provider `plan_updated` as telemetry, not as the durable or editable execution-plan model.
- Rejected a separate generic policy layer because it would duplicate ai-inst; instead established ai-inst as the authoritative source for durable project guidance and constrained routines to declare which ai-inst modules or loadouts they need.
- Agreed that routine-pack-level tool dependencies should be removed from the MVP and that dependencies should be owned by individual routines.
- Identified that the original execution `mode` concept was underspecified and should be split into `executionKind` and `delegationPolicy` to distinguish logical shape from delegation permissions.
- Moved concrete model selection out of per-routine policy and up to routine-pack-level model routing, with routines referring only to workload classes.
- Refined instruction loading so routines request selective ai-inst module loadouts rather than binary load-all toggles, reducing unnecessary context for subagents.
- Defined hooks as references either to built-in runtime system actions or to other routines, rejecting free-form hook prompts and raw shell snippets as the default shared-pack mechanism.
- Distinguished ephemeral runtime outputs from durable artifacts and reaffirmed that durable history, verification, and documentation should flow through project-memory rather than a parallel artifact store.
- Mapped the user's habitual project workflow onto candidate routines spanning idea clarification, scope shaping, foundation docs, MVP work-item planning, per-item implementation, verification, review, and follow-up triage.

## Follow-up

- Design and implement the MVP routine-pack domain model in code, including routine definitions, pack-level model routing, instruction loadouts, hook references, and runtime system-action references.
- Author the first routine pack that mirrors the user's real project workflow from idea clarification through work-item implementation and follow-up triage.
- Later add a stable canonical guidance surface for routine-pack architecture if the domain model stabilizes beyond the initial decision and implementation slices.
