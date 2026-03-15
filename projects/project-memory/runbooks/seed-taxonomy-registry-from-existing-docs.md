---
date: 2026-03-15
project: project-memory
topic: seed-taxonomy-registry-from-existing-docs
source: user
status: active
---
# Runbook

## Purpose

Build the first taxonomy registry for an existing project by deriving initial registered topics and scopes from current authoritative material before normal registry-backed validation is enforced.

## Procedure

- Inventory existing active canonical documents and any repo-local documentation that still acts as an authoritative source of truth.
- Group discovered material by semantic area and proposed authority boundary, then identify candidate registered topics, scopes, aliases, authority locations, migration states, and lifecycle states.
- Record explicit ambiguities where historical material does not support a clean one-to-one mapping between topic and scope.
- Create or update the taxonomy registry with the seeded entries, keeping unresolved cases visible rather than silently normalizing them.
- Review seeded entries for duplicate active authority claims, overly broad scopes, and places where aliases are standing in for real topic splits or renames.
- Only after the seeded registry is acceptable, enable normal registry-backed validation for non-registry canonical documents.

## Verification

- Confirm every discovered authoritative scope is represented in the registry or explicitly recorded as unresolved.
- Confirm each seeded entry has authority location and migration status.
- Confirm conflicting or ambiguous historical structures are flagged for follow-up instead of being hidden.
- Confirm the resulting registry is sufficient for normal canonical-document validation to run deterministically.
