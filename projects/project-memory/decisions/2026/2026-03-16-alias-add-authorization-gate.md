---
date: 2026-03-16
project: project-memory
topic: alias-add-authorization-gate
source: user
status: active
---
# Decision

## Context

The taxonomy authority model defines alias-add as an explicit taxonomy change, and the taxonomy governance enforcement decision explicitly gates introduction of new registered topics and scopes behind either explicit user confirmation or an already-authorized work item or decision. However, the existing enforcement wording does not state that alias-add uses the same authorization gate. That leaves room for agents to misread alias creation as a lightweight compatibility edit instead of a control-plane taxonomy change. Because aliases affect registry-backed name resolution and can change which canonical-doc scope names are treated as valid, the authorization rule needs to be explicit.

## Decision

Treat alias-add as an authorized taxonomy change that uses the same gate as introducing a new registered topic or scope. Agents must not add or modify taxonomy aliases unless explicit user confirmation exists or an already-authorized work item or decision clearly directs the alias change. This decision clarifies the governance contract established by the taxonomy-registry-authority-model and taxonomy-governance-enforcement-and-surfaces decisions without superseding them.

## Consequences

- Alias additions are not allowed as opportunistic compatibility edits during ordinary canonical-doc work.
- Registry updates that add or change aliases require the same level of authorization evidence expected for new registered topics or scopes.
- Future taxonomy audit and write-path behavior can rely on an explicit governance rule instead of inference from the broader taxonomy model.
