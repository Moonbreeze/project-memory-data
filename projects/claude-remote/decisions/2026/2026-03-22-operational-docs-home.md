---
date: 2026-03-22
recorded_at: 2026-03-22T09:31:09.457Z
project: claude-remote
topic: operational-docs-home
source: agent
status: archived
---
# Decision

## Context

The repository accumulated repo-local operational markdown files during the multi-provider migration because the work needed a temporary place for live verification checklists, feasibility notes, and session backlog tracking. The project already uses project-memory for durable runbooks, provider notes, decisions, and planning context, and keeping both repo docs and managed docs as active operational sources now creates duplication and drift risk.

## Decision

Use project-memory as the authoritative home for operational documentation for this project. Keep the repository-level `MULTI_PROVIDER_REFACTOR_PLAN.md` and the test-facing `src/__tests__/KNOWN_BUGS.md` in the repo, but move repo-local operational guides such as live verification checklists, feasibility notes, and migration backlog tracking into managed runbooks, provider notes, and work items.

## Consequences

- Future operational updates should go to project-memory managed documents instead of adding new repo-local docs under `docs/` for the same purpose.
- The architecture plan and test-owned bug registry remain in the code repository because they are part of the source tree and test workflow rather than purely operational guidance.
- Planning state should live in project-memory work items so bounded planning reads surface the real executable backlog.
- Repo-local operational docs that duplicate managed guidance should be removed or reduced to non-authoritative pointers to avoid drift.

## Stable Guidance Review

- Outcome: reviewed-no-change
- Summary: Reviewed current stable guidance and determined no update was required.
