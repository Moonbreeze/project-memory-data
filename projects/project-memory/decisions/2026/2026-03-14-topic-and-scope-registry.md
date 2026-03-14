---
date: 2026-03-14
project: project-memory
topic: topic-and-scope-registry
source: user
status: active
---
# Decision

## Context

The baseline scenario and lifecycle work showed that topic and scope are no longer acting as simple labels on documents. They are becoming the control plane for authoritative canonical docs, partial documentation migration, read entrypoints, and future cross-project relationships. Without a shared categorization source of truth, the project cannot reliably prevent overlapping canonical coverage or guide narrow reads.

## Decision

Treat topic categorization as a first-class project-information layer. Keep scope as the authority boundary attached to a topic, and maintain the source of truth for topic, scope, aliases, authority ownership, migration status, and explicit cross-project mappings in a canonical registry document before introducing a dedicated document type for taxonomy.

## Consequences

- Canonical documentation should be assigned to declared authoritative scopes rather than to informal free-form topics.
- The model should enforce at most one active authoritative canonical document per scope, with overview documents linking outward instead of competing for authority.
- Partial migration from repository docs into project-memory becomes manageable because authority can be stated per topic or scope.
- Read entrypoints can resolve through the registry layer to the current authoritative documents without scanning unrelated material.
- Cross-project topic relationships are allowed, but they remain explicit mappings and do not automatically widen the default read scope.
