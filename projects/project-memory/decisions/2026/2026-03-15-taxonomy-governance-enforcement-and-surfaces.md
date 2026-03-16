---
date: 2026-03-15
project: project-memory
topic: taxonomy-governance-enforcement-and-surfaces
source: user
status: active
---
# Decision

## Context

After defining the taxonomy authority model, the project still needed explicit enforcement and surface rules. Canonical documents must be validated against the taxonomy registry, agents must not expand taxonomy implicitly, and the operational contract must stay coherent across shared core logic, CLI, and MCP. The project also needs a clear place for procedural guidance so governance workflows do not get duplicated as local runbooks in every downstream repository.

## Decision

Enforce taxonomy consistency in two modes: mandatory semantic validation on canonical-document write paths, and separate audit flows for bootstrap, migration, and taxonomy-registry changes. A non-registry canonical document may be created or updated only when its declared registry scope already exists in the active taxonomy registry. Agents must not introduce a new registered topic or scope unless explicit user confirmation exists or an already-authorized work item or decision clearly directs the taxonomy change. Implement taxonomy invariants in shared core logic so they apply equally to CLI and MCP. Any behavior that defines model correctness, write acceptance, reserved registry semantics, or taxonomy validation must not live only in MCP-facing orchestration. Expose taxonomy-changing workflows through both CLI and MCP when they represent first-class managed operations. MCP may lead in interactive guidance and conversational orchestration, but CLI must not lag behind in capability or model enforcement. Describe operational taxonomy procedures as tool-level meta-runbooks by default; use project-local runbooks only when a specific project intentionally diverges from the default system procedure.

## Consequences

- Registry-backed canonical validation becomes a model invariant instead of an agent convention.
- Unknown scopes and topics fail explicitly rather than being guessed from local context.
- Taxonomy expansion requires explicit authorization instead of happening as a side effect of canonical-document creation.
- CLI and MCP remain two surfaces over one shared model rather than drifting into separate semantics.
- Bootstrap, migration, and taxonomy-change audits become explicit operational moments instead of ad hoc cleanups.
- Operational procedure lives in centralized tool-level guidance instead of being duplicated in every managed project by default.
- Current duplicate-authority enforcement on canonical-document writes performs a full scan of active project canonical docs; treat that as an intentional current limitation until scale pressure justifies a dedicated index or caching model.
