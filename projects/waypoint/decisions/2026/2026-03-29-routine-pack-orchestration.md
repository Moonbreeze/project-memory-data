---
date: 2026-03-29
recorded_at: 2026-03-29T10:38:44.953Z
project: waypoint
topic: routine-pack-orchestration
source: agent
status: active
---
# Decision

## Context

Waypoint currently has provider-backed sessions, provider-neutral events, and transport delivery, but it does not yet have a first-class orchestration surface for reusable execution patterns. The existing provider `plan_updated` stream is telemetry emitted by a running model, not a user-editable or reusable execution description. The user wants a way to solve free-form chat requests through reusable subagent patterns, while still choosing models, loading project instructions deliberately, and preserving durable project documentation.

During the architecture discussion, we rejected two extremes:
- a fully deterministic pre-authored step list as the only execution model, because it fits poorly with user requests stated as goals in chat rather than as workflows;
- a fully unconstrained coordinator that may invent arbitrary subagent actions, because that would make behavior, cost, and side effects too hard to predict or audit.

The resulting direction is a hybrid: an agent-coordinator interprets the user goal, but it may invoke only typed reusable routines from shareable routine packs. The coordinator remains responsible for selecting which routine to call, while the routine contracts bound the possible execution shapes.

We also clarified the integration boundaries with existing project systems. `ai-inst` already serves as the durable source of project instructions and must not be duplicated by a separate generic policy engine. `project-memory` already serves as the durable documentation and evidence store and must remain the authoritative sink for session history, verification, decisions, runbooks, and similar records. Runtime orchestration should respect those systems rather than replacing them.

Several modeling details were refined during discussion:
- routine-pack-level tool dependencies are unnecessary in the MVP; routine dependencies belong to individual routines and can be aggregated upward if needed for display;
- the original `RoutineExecutionConfig.mode` proposal was too ambiguous because it mixed logical execution shape with delegation rights; the model should instead separate `executionKind` from `delegationPolicy`;
- routines should not hardcode concrete models; they should refer to workload classes, while concrete model routing should live at the routine-pack level with room for later user or environment overrides;
- instruction loading for subroutines should be module-based and selective, not a binary load-all-or-load-none flag, so subagents receive only the ai-inst modules they need;
- hooks must not be free-form agent instructions or raw shell text; they should resolve either to typed runtime system actions or to calls into other routines;
- runtime primitives such as loading ai-inst modules, spawning or waiting for sessions, and writing durable project-memory records must be defined by Waypoint itself as built-in runtime actions rather than by arbitrary pack-authored shell commands.

## Decision

Introduce a dedicated orchestration layer in Waypoint built around an agent-coordinator and typed reusable routine packs.

The coordinator accepts free-form user goals stated in chat, analyzes them, and compiles them into invocations of registered routines. The coordinator may not invent arbitrary execution primitives; it can only call routines and built-in runtime actions known to the system.

A routine pack is a shareable declarative bundle of routines plus pack-level model routing. Each routine defines when it should be used, what inputs it expects, what outputs it must return, what ai-inst instruction loadout it requires, what workload class it targets, and what deterministic hooks or runtime actions are involved in execution.

`ai-inst` remains the authoritative source of durable project guidance. Routine packs do not introduce a second generic policy layer for project rules. Instead, routines declare which ai-inst modules or loadouts they require so the runtime can inject the correct project guidance into a subroutine without overloading it with unrelated instructions.

`project-memory` remains the authoritative durable record system for session history, verification evidence, decisions, runbooks, and related documentation. Routine runtime outputs may be ephemeral, but durable artifacts are expected to flow through project-memory rather than a parallel documentation surface.

Runtime primitives used by routines are built into Waypoint. Hooks and routine steps may refer to typed built-in system actions such as ai-inst module loading, session spawning, waiting for subruns, or project-memory record creation, but they must not be represented as arbitrary shell commands in shared routine-pack configuration.

The routine execution model separates two concerns:
- `executionKind` describes whether a routine is a single logical unit or a composite routine orchestrated from multiple internal calls;
- `delegationPolicy` describes whether delegation to subagents or child runs is forbidden, allowed, or required.

Concrete model choice is not encoded directly on each routine. Routines reference workload classes such as cheap analysis, balanced implementation, or deep architecture, and the routine pack maps those classes to specific provider/model selections. This keeps routine semantics stable while allowing pack-specific and later user-specific model routing policies.

For the MVP, pack-level tool dependency declarations are omitted. Dependencies are declared at the routine level only.

## Consequences

- Waypoint will need new domain types for routine packs, routine definitions, execution runs, instruction loadouts, workload classes, hook references, and runtime system-action references.
- The existing provider `plan_updated` event remains runtime telemetry from providers and does not become the source of truth for reusable orchestration patterns.
- Future subagent execution must be explainable in terms of registered routines and built-in runtime primitives rather than opaque coordinator improvisation.
- ai-inst stays the single authoritative place for durable project guidance, so orchestration work should integrate with ai-inst instead of introducing a competing project-policy surface.
- project-memory stays the durable sink for history and evidence, so orchestration work should distinguish ephemeral run artifacts from durable records and route the latter through project-memory.
- Routine configuration must model execution shape and delegation as separate concerns, preventing the ambiguity identified in the earlier single `mode` proposal.
- Shared routine packs should reference workload classes instead of concrete models, which pushes concrete provider/model mapping into pack-level routing and later override layers.
- Because runtime primitives are defined by Waypoint rather than by pack-authored shell snippets, shared packs remain more portable, auditable, and safe to execute.
- The first implementation slices should focus on the routine-pack domain model and on one pack that mirrors the user's actual workflow before building a broader general coordinator runtime.

## Stable Guidance Review

- Outcome: update-required
- Summary: Reviewed current stable guidance and identified a follow-up update requirement.
- Note: This decision establishes new stable orchestration guidance, but the project does not yet have a canonical stable-guidance surface for routine-pack architecture. The decision is recorded now so the rationale is durable, and follow-up implementation/documentation work should later add or update the stable guidance surface once the domain model settles.
