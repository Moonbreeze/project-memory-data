---
date: 2026-03-29
recorded_at: 2026-03-29T10:49:24.989Z
project: waypoint
topic: routine-pack-authoring-surfaces
source: agent
status: active
---
# Decision

## Context

The 2026-03-29 `routine-pack-orchestration` decision established routine packs as a user-editable orchestration surface with pack-level routing, selective ai-inst loadouts, typed hooks, and durable outputs routed through project-memory. That architecture grew out of a runtime whose current UX is centered on single provider-backed sessions in Telegram. Telegram remains effective for operational session work such as starting turns, watching progress, handling approvals, and resuming active sessions, but it is a weak primary environment for authoring and revising structured routine and routine-pack configuration. Routine-pack authoring needs richer affordances for editing, validation, diffing, previewing, and understanding routing and hook relationships. Waypoint already has a provider-neutral Web transport and server for session flows, which makes a richer dedicated interface feasible without re-centering the architecture on Telegram commands. We also need to avoid treating MCP as a UI substitute: MCP is useful as a programmatic and IDE-facing integration surface, but it does not replace a human-oriented authoring interface for complex orchestration configuration.

## Decision

Separate routine-pack UX into two primary surfaces. Telegram remains the operational surface for live session work: starting or resuming sessions, sending free-form goals, monitoring event streams, and responding to approvals. Routine and routine-pack creation, inspection, editing, validation, preview, and publishing should use a dedicated authoring surface, with Web UI as the primary human-facing MVP. MCP may be exposed later as a secondary integration surface for IDE or agent-driven editing against the same provider-neutral orchestration API, but it is not the primary human authoring interface. The authoring surface must sit on top of provider-neutral routine-pack domain and API boundaries rather than embedding authoring logic into transport-specific handlers.

## Consequences

- Waypoint needs an explicit authoring API and supporting domain concepts for routine-pack drafts, validation, preview, inspection, and publish flows instead of relying on Telegram message exchanges as the primary editing mechanism.
- Telegram UX can stay optimized for operational runtime flows without being overloaded with complex configuration editing and review interactions.
- Web transport and future Web UI become the primary path for human routine-pack authoring, so upcoming routine-pack work should account for screen-oriented configuration and validation workflows.
- MCP should be designed as a secondary integration surface over the same orchestration API so IDE or agent clients can automate authoring tasks without creating a separate source of truth.
- The routine-pack domain model MVP should be evaluated not only for runtime expressiveness but also for whether it is editable, validatable, and previewable in a dedicated authoring interface.
- The first concrete routine-pack example should be shaped so it can be authored and inspected through the future authoring surface rather than assuming Telegram is the main place where packs are configured.

## Stable Guidance Review

- Outcome: update-required
- Summary: Reviewed current stable guidance and identified a follow-up update requirement.
- Note: This decision refines the stable routine-pack direction by adding an explicit UX-surface split, but the project still has no canonical stable-guidance document for routine-pack architecture. A future canonical update should consolidate the orchestration and authoring-surface decisions once the MVP domain and authoring API settle.
