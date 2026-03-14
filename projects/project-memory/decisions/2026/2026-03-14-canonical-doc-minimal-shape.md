---
date: 2026-03-14
project: project-memory
topic: canonical-doc-minimal-shape
source: agent
status: active
---
# Decision

## Context

Session 2 required minimal canonical-doc support in the project-memory tool repo while explicitly avoiding a broader taxonomy-model redesign. Session 1 already fixed the taxonomy-registry baseline as the source of topic slug, authoritative scope boundary, authority location, migration status, aliases, related topics, and explicit cross-project mappings.

## Decision

Introduce `canonical-doc` as a managed document type with minimal shape: store canonical docs at `projects/<project>/canonical-docs/<registry_scope>/<topic>.md`, require `registry_scope` in frontmatter as the declared taxonomy-registry scope boundary, use a simple Summary/Guidance/References body template, and implement write behavior as upsert rather than immutable append.

## Consequences

- Canonical docs are linked to the declared registry scope without reopening or generalizing the taxonomy model in Session 2.
- The design is intentionally narrow and compatible with future expansion in Session 3+, including richer canonical-doc schemas or stronger registry-backed validation.
- Existing document types, list/search/read behavior, and backlog preset remain unchanged apart from supporting one additional managed type.
- Git commit enforcement needs a dedicated `docs(canonical)` scope so canonical-doc-only changes stay auditable without falling back to `mixed`.
