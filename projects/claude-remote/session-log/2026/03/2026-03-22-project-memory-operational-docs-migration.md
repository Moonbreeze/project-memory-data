---
date: 2026-03-22
recorded_at: 2026-03-22T09:31:26.777Z
project: claude-remote
topic: project-memory-operational-docs-migration
source: agent
status: active
---
# Session Note

## Summary

Migrated the repo-local operational docs into project-memory, expanded managed runbooks/provider notes to replace the old markdown files, created explicit work-item backlog entries for the remaining migration tasks, and removed duplicated repo docs under docs/.

## Actions

- Created an in-progress work item for the documentation migration slice.
- Updated the managed runbooks `live-smoke-verification`, `manual-live-verification`, and `remaining-migration-sessions` so they replace the deleted repo-local operational docs.
- Updated the `codex-app-server` provider note with the feasibility guidance that previously lived in repo docs.
- Created work items for the remaining backlog slices: `codex-feasibility-artifacts`, `manual-live-verification-closure`, and `migration-final-cleanup-closure`.
- Created the `operational-docs-home` decision to make project-memory the authoritative home for operational docs.
- Deleted the duplicated repo-local docs `docs/README.md`, `docs/codexFeasibility.md`, `docs/liveSmokeTests.md`, `docs/manualVerification.md`, and `docs/nextSessions.md`.

## Follow-up

- Close the remaining blocked work items when the missing Codex feasibility artifacts and manual live verification evidence are recorded.
- If contributors still need an in-repo pointer for project-memory usage, add a short non-authoritative note later rather than restoring duplicated operational docs.
