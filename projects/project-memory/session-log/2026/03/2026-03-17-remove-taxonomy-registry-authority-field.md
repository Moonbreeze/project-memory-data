---
date: 2026-03-17
project: project-memory
topic: remove-taxonomy-registry-authority-field
source: agent
status: active
---
# Session Note

## Summary

Removed the taxonomy registry authority field from the runtime model after confirming it was semantically ambiguous and not used by write resolution, bounded reads, or search.

## Actions

- Removed `authority` from taxonomy registry entry types, parsing, serialization, bootstrap data, and reserved-entry validation in the tool repo.
- Updated CLI and MCP upsert-taxonomy-registry surfaces so registry entries no longer accept or require `authority`.
- Updated fixtures and tests to the new registry entry shape and verified targeted taxonomy-related test suites passed.

## Follow-up

- Update the taxonomy-registry-authority-model decision to reflect that `authority` is no longer part of the current registry schema and remains only a possible future extension if a distinct use case appears.
