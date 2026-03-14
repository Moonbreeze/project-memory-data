---
date: 2026-03-14
project: project-memory
topic: near-term-implementation-sessions
source: agent
status: active
---
# Runbook

## Purpose

Define the next implementation sessions for evolving project-memory from the current planning baseline into canonical-doc, read-entrypoint, and work-item support without reopening the domain model each time.

## Procedure

- Session 1, taxonomy registry: define the first canonical registry artifact for topic and scope categorization, including authoritative scope boundaries, aliases, migration status, related topics, and explicit cross-project mappings.
- Session 2, minimal canonical-doc support: implement the first canonical-doc document type with path and layout rules, template, upsert semantics, validation, list/read/search support, and links back to the taxonomy registry.
- Session 3, project-scoped doc commit protocol: implement project-aware managed-doc commit semantics in `project-memory`, including `docs(<project>/<scope>): <summary>`, default single-project batching, and the validation needed for later automatic commit-per-write flows.
- Session 4, read entrypoints phase 1: implement the first bounded read flows for cold start, topic lookup, and rationale lookup so agents can reach the current truth without broad project scans.
- Session 5, work-item spec: finalize the future work-item schema, lifecycle, provenance model, dependency metadata, planning states, and relationships to decisions, canonical docs, session notes, and verification results.
- Session 6, work-item implementation: implement the first work-item document type and the initial backlog or planning flows, including dependency-aware ready versus blocked interpretation and basic close or archive semantics.
- Session 7, lifecycle and cross-project helpers: add the next layer of lifecycle operations, partial migration helpers, and explicit cross-project link handling after the core document types and read flows are stable.

## Verification

- The session plan starts with categorization and authority before introducing canonical-doc and work-item execution layers.
- Project-aware commit semantics are implemented before automatic managed-doc commit flows so history remains readable by project and scope.
- Read entrypoints are implemented before full work-item rollout so the project gains retrieval value early.
- Work-item design and implementation explicitly include provenance and dependency handling rather than treating them as follow-up details.
- Later lifecycle and cross-project helpers build on stable document and read models instead of compensating for missing foundations.
