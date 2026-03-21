---
date: 2026-03-21
recorded_at: 2026-03-21T00:00:00.000Z
project: project-memory
topic: taxonomy-registry
registry_scope: taxonomy-registry
source: user
status: active
---
# Canonical Doc

## Summary

Active taxonomy registry for the project-memory project, including a dedicated repository-documentation scope separated from the broader system scope.

## Guidance

- registry-entry: scope=document-model; topic=document-model; state=active; migration=create-topic; aliases=none; mapped-scopes=none
- registry-entry: scope=reads; topic=bounded-read-model; state=active; migration=create-topic; aliases=none; mapped-scopes=none
- registry-entry: scope=repository-documentation; topic=repository-documentation-strategy; state=active; migration=split; aliases=none; mapped-scopes=system
- registry-entry: scope=system; topic=system-overview; state=active; migration=boundary-change; aliases=none; mapped-scopes=repository-documentation
- registry-entry: scope=taxonomy-registry; topic=taxonomy-registry; state=active; migration=create-topic; aliases=none; mapped-scopes=none
- registry-entry: scope=work-item-planning; topic=work-item-planning-model; state=active; migration=create-topic; aliases=none; mapped-scopes=none

## References

- decision: taxonomy-registry-authority-model
- runbook: bootstrap-taxonomy-registry
- canonical-doc: system-overview
- canonical-doc: repository-documentation-strategy
