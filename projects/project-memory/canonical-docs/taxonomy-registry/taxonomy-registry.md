---
date: 2026-03-29
recorded_at: 2026-03-29T06:20:14.913Z
project: project-memory
topic: taxonomy-registry
registry_scope: taxonomy-registry
source: agent
status: active
---
# Canonical Doc

## Summary

Active taxonomy registry for the project-memory project, including dedicated repository-documentation and Web UI scopes separated from the broader system scope.

## Guidance

- registry-entry: scope=document-model; topic=document-model; state=active; migration=create-topic; aliases=none; mapped-scopes=none
- registry-entry: scope=reads; topic=bounded-read-model; state=active; migration=create-topic; aliases=none; mapped-scopes=none
- registry-entry: scope=repository-documentation; topic=repository-documentation-strategy; state=active; migration=split; aliases=none; mapped-scopes=system
- registry-entry: scope=system; topic=system-overview; state=active; migration=boundary-change; aliases=none; mapped-scopes=repository-documentation
- registry-entry: scope=taxonomy-registry; topic=taxonomy-registry; state=active; migration=create-topic; aliases=none; mapped-scopes=none
- registry-entry: scope=web-ui; topic=read-only-web-ui-guidance; state=active; migration=create-topic; aliases=none; mapped-scopes=none
- registry-entry: scope=work-item-planning; topic=work-item-planning-model; state=active; migration=create-topic; aliases=none; mapped-scopes=none

## References

- decision: taxonomy-registry-authority-model
- decision: web-search-route-and-collapsible-control-pattern
- runbook: bootstrap-taxonomy-registry
- canonical-doc: system-overview
- canonical-doc: repository-documentation-strategy
