---
date: 2026-03-21
recorded_at: 2026-03-21T00:00:00.000Z
project: project-memory
topic: historical-recorded-at-backfill-policy
source: user
status: active
---
# Decision

## Context

`recorded_at` is already implemented as the managed document timeline key for new and rewritten documents, while older documents without explicit `recorded_at` still sort through a deterministic fallback derived from `date`. A follow-up work item asked whether the project should reconstruct historical intra-day timestamps for older documents so future chronological queries or a human-facing Web UI could rely on more accurate same-day ordering. Review of the current implementation showed that the existing fallback remains deterministic and backward compatible, but no trustworthy repository-wide source currently exists for reconstructing historical write time with sufficient confidence. Git history can preserve some chronology signals, yet rebases, squashes, imports, and branch movement make it an unreliable source of semantic document-record time for managed records.

## Decision

Do not perform a repository-wide historical backfill of `recorded_at` for older managed documents at this time. Keep the current deterministic `date`-derived fallback as the official backward-compatible strategy for historical documents that lack explicit `recorded_at`. Allow targeted manual enrichment of `recorded_at` only when a document has a trustworthy direct source for the original timestamp, rather than an inferred timestamp reconstructed from Git metadata alone. Revisit this policy only if a future product surface such as the planned Web UI or a query contract introduces a concrete requirement for trustworthy same-day ordering of historical documents and the project also has an acceptable evidence source and guardrails for filling those timestamps honestly.

## Consequences

- The project keeps deterministic and stable historical ordering without paying the cost of a migration that would manufacture false precision.
- New and updated documents continue to capture precise `recorded_at`, while older documents remain explicitly day-granular unless trustworthy evidence exists for manual enrichment.
- Future human-facing timeline or Web UI work must distinguish between exact recorded timestamps and fallback day-level chronology rather than assuming all historical ordering is equally precise.
- Any future historical backfill effort now requires an explicit product need, a trustworthy timestamp source, and defined guardrails before implementation begins.

## Stable Guidance Review

- Outcome: reviewed-no-change
- Summary: Reviewed current stable guidance and determined no update was required.
