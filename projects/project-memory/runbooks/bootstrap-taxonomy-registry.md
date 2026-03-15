---
date: 2026-03-15
project: project-memory
topic: bootstrap-taxonomy-registry
source: user
status: active
---
# Runbook

## Purpose

Create the reserved taxonomy registry canonical document during project bootstrap so every project starts with a valid taxonomy authority surface and the bootstrap circularity is resolved explicitly.

## Procedure

- Determine the reserved project-level scope and topic for the taxonomy registry from the shared system constants and bootstrap contract.
- Create the reserved registry canonical document at its deterministic path during bootstrap before any other canonical-document write requires registry-backed validation.
- Treat the reserved registry scope as a bootstrap primitive for this creation flow only; do not require prior self-registration when creating the registry document itself.
- Populate the initial registry body with the minimum structure needed to record registered topics, scopes, authority ownership, migration status, lifecycle state, aliases, and explicit mappings.
- Mark the registry document active and ensure no second active registry surface exists for the same project.
- Return the created registry path and reserved scope/topic values so follow-on tooling can rely on them immediately.

## Verification

- Confirm the reserved registry document exists at the expected managed canonical-doc path.
- Confirm the registry document is active and is the only active registry surface for the project.
- Confirm bootstrap accepted the registry creation without requiring prior self-registration of the reserved registry scope.
- Confirm subsequent canonical-document writes can resolve the registry surface for the project.
