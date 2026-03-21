---
date: 2026-03-21
recorded_at: 2026-03-21T00:00:00.000Z
project: project-memory
topic: project-scoped-managed-commit-selection
source: agent
status: active
---
# Decision

## Context

The current commit_pending_changes flow scans all pending managed-document changes under projects/ and archives/ and rejects the batch when more than one project is represented. In practice, the memory repository is often used for parallel work across multiple projects, so this global multi-project rejection pushes users back to direct git staging and manual commits whenever unrelated pending changes coexist in the same worktree. That bypass reduces the value of the managed commit lifecycle and makes the tool fit a single-project worktree model that does not match normal operation.

## Decision

Replace the current global multi-project rejection with an explicit project-scoped commit contract. commit_pending_changes must accept a target project and commit only pending managed-document changes for that project, while pending changes for other projects in the same repository are ignored rather than treated as an error. Preserve project-level atomicity and continue to forbid arbitrary path-level partial managed commits. Remove the old semantics, error model, and tests that treat a multi-project pending tree as invalid by default.

## Consequences

- Managed commits become usable again in a shared multi-project memory repository without requiring fallback to direct git commands for routine project isolation.
- The API contract becomes explicit: project selection is an input parameter rather than an inferred property of the entire pending tree or a side effect of the commit message.
- Validation remains strict at the project boundary: the requested project must have pending managed-document changes, and the commit message project must match the selected project.
- Legacy tests and descriptions that encode multi-project pending changes as an automatic error must be removed or replaced with project-scoped behavior checks.

## Stable Guidance Review

- Outcome: reviewed-no-change
- Summary: Reviewed current stable guidance and determined no update was required.
