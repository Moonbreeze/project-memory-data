---
date: 2026-03-14
project: project-memory
topic: authority-migration-and-archive-policy-baseline
source: agent
status: archived
---
# Runbook

## Purpose

Refine the baseline policy for authoritative scope ownership, partial migration, and archive transitions so future canonical-doc and work-item support can implement lifecycle behavior consistently.

## Procedure

- Authority ownership rule: every canonical doc must map to a declared topic scope, and only one active canonical doc may be authoritative for that scope at a time. Overview or index-style docs should link to authoritative scope docs rather than compete with them.
- Conflict resolution rule: if two canonical docs claim the same authoritative scope, treat it as a modeling error. Resolve it by narrowing scopes, splitting an overly broad doc, or superseding the older authoritative document when one truly replaces the other.
- Partial migration rule: repository docs and project-memory canonical docs may coexist during migration, but the authoritative location must be declared per topic scope. A project may remain in a partial migration state as long as each migrated scope clearly points to its current source of truth.
- Work-item archive rule: work items should move through open, in-progress, blocked, done, or canceled states before archival. Archive only after done or canceled when the item is no longer needed in active planning, not immediately at the moment of completion.
- Canonical-doc archive rule: mark a canonical doc as superseded when a newer authoritative doc replaces it for the same scope. Use archived only when the scope is retired, intentionally removed from the active knowledge base, or the document was transitional and is no longer part of the living corpus.
- Cross-project relationship rule: cross-project references may connect related topics, but they do not change authority ownership inside the current project unless an explicit mapping says so.

## Verification

- The policy distinguishes replacement from retirement for canonical documentation.
- Partial migration has a controlled steady state instead of requiring an all-at-once cutover.
- Future work-item close and archive operations can be implemented against explicit lifecycle criteria.
- Authoritative scope conflicts can be detected and resolved consistently before they leak into read or write workflows.
