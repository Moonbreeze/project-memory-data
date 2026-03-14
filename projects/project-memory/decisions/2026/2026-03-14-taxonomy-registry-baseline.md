---
date: 2026-03-14
project: project-memory
topic: taxonomy-registry-baseline
source: agent
status: active
---
# Decision

## Context

The current document model treats topic as a document label and scope only as a free-form field inside verification records. That is not enough for the next phases of canonical-doc support, bounded read entrypoints, and partial migration from repository docs.

The planning baseline already requires a shared source of truth for topic categorization, authority ownership, migration state, and explicit cross-project mappings before canonical docs are introduced. Without that registry layer, canonical coverage and read narrowing would depend on informal naming and agent memory.

## Decision

Use one managed registry artifact as the temporary source of truth for topic and scope categorization during Session 1. Store it as a runbook-shaped managed document for now, and define a stable entry schema that canonical-doc support can later consume without reopening the taxonomy model.

Each registry entry must describe the topic slug, authoritative scope boundary, optional aliases, current migration status, related topics, explicit cross-project mappings, and authority notes when the source of truth still lives outside project-memory.

The registry is descriptive rather than executable: it does not itself become the canonical doc for a topic, it declares where authority belongs, and it prevents overlapping or ambiguous scope ownership before canonical docs are added.

## Consequences

- Session 1 can land a real managed artifact without waiting for a new canonical-doc document type.
- Session 2 can implement canonical docs against a predeclared scope and authority model instead of inventing one during write-path work.
- Topic lookup and bounded read entrypoints can later resolve through stable scope metadata instead of scanning decisions and session history.
- Partial migration becomes explicit because each topic can declare whether its authoritative source is already in project-memory, still in repo docs, or split across locations during transition.
- Cross-project relationships stay opt-in and explicit rather than widening default reads automatically.
