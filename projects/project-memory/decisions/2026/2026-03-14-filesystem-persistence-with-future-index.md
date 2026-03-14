---
date: 2026-03-14
project: project-memory
topic: filesystem-persistence-with-future-index
source: user
status: active
---
# Decision

## Context

The document model is growing in complexity: topic and scope registry, cross-document relationships, multiple read entrypoints, and future work-item support. This raises the question of whether filesystem-based persistence should be replaced with a database such as MongoDB. However, current data volumes are modest (tens to hundreds of documents), access patterns are simple scans with frontmatter filtering, and the filesystem provides critical advantages: transparency (readable and editable without tooling), free git history and diffs, and zero-server architecture suitable for a CLI-first tool.

## Decision

Keep the filesystem with markdown and frontmatter as the sole source of truth. Do not migrate to a database. If data volumes grow significantly (thousands of documents) or scan-based reads become a performance bottleneck, add a SQLite index built on top of the existing files rather than replacing the storage layer. The index must be a rebuildable derived artifact, not a separate source of truth.

## Consequences

- Filesystem transparency, git history, and serverless operation are preserved as architectural invariants.
- No database server dependency is introduced into the runtime or deployment.
- A future SQLite index would accelerate queries without changing the storage model — files remain authoritative, the index is rebuilt from them.
- The decision should be revisited only when concrete evidence appears: thousands of documents, measurable scan latency, or real multi-user concurrent write scenarios.
- Migration to a full database (MongoDB, Postgres, etc.) is explicitly ruled out unless the revisit criteria are met and the index approach proves insufficient.
