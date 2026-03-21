---
date: 2026-03-17
project: project-memory
topic: document-timeline-and-latest-first-query-defaults
source: user
status: active
---
# Decision

## Context

The managed document model currently supports only a day-level `date` field and falls back to repository path ordering when multiple documents share the same day. That is insufficient for newest-within-day questions, future human-facing timeline views, and any query surface that should prefer the latest relevant records by default. At the same time, path layout and day-level date semantics are already embedded in document paths, bounded-read explanations, and existing stored documents, so the project needs a timeline model that adds intra-day ordering without forcing an immediate full historical migration or redefining what `date` means. Review of the current query surfaces also showed that ordinary `listDocuments` defaults to path-ascending order, while `searchDocuments` currently returns filtered results in traversal order rather than an explicit latest-first or relevance-aware order. With the current search model still based on simple substring matching rather than ranked retrieval, chronology should be the primary default ordering unless a caller explicitly asks for another sort.

## Decision

Add an explicit `recorded_at` frontmatter field to the managed document model as the document timeline key for intra-day ordering. Keep `date` as the day-level bucket and path key; do not replace it with `recorded_at`. Treat timeline-aware chronological ordering as `date`, then `recorded_at`, then `relativePath`, with descending order representing newest-first and ascending order representing oldest-first. For stored documents that do not yet declare `recorded_at`, use a deterministic fallback derived from `date` so the model remains backward compatible until any later backfill work is authorized. Change ordinary list-query defaults to latest-first chronology: `listDocuments` should default to date-based descending order rather than path-ascending order, while `path` sort remains available as an explicit opt-in for audit and filesystem-oriented inspection. Extend the same latest-first default to `searchDocuments` in the current substring-search model, because there is no independent relevance ranking yet; if a future search implementation introduces a real relevance score, chronology should become a tie-break rather than the primary default. Apply the new timeline semantics only to query and bounded-read surfaces whose contract is chronological or planning-ranked; stages explicitly documented as path-ordered must keep path ordering unchanged. Do not require an immediate repository-wide migration of existing managed documents as part of adopting this model.

## Consequences

- The managed model can answer newest-within-day questions without depending on path-name accidents or filesystem metadata.
- Existing documents remain readable and sortable without an immediate mandatory backfill, but historical same-day ordering stays coarse until an explicit migration or manual enrichment is authorized.
- Chronological query surfaces become more aligned with user expectations because ordinary list and current search defaults now prefer the latest records.
- `path` ordering remains available for deterministic low-level inspection instead of being the implicit default for ordinary list usage.
- Bounded-read contracts stay explicit: path-ordered stages remain path-ordered, while recent/newest/planning-ranked stages can adopt timeline-aware chronology without widening their scope.
- A future relevance-ranked search model can reuse `recorded_at` as a chronology tie-break instead of redefining timeline semantics again.

## Stable Guidance Review

- Outcome: updated
- Summary: Updated stable guidance by adding explicit timeline and `recorded_at` ordering semantics to the active document-model and bounded-read canonical docs, including the rule that explicitly path-ordered stages remain path-ordered.
