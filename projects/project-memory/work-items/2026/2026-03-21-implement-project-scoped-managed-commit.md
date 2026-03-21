---
date: 2026-03-21
recorded_at: 2026-03-21T00:00:00.000Z
project: project-memory
topic: implement-project-scoped-managed-commit
source: agent
status: active
work_item_state: done
---
# Work Item

## Summary

Implement project-scoped managed commits with generated commit subjects and remove the old multi-project pending-tree rejection contract.

## Outcome

The project-memory commit flow accepts an explicit project selector and free-text summary, commits only pending managed-document changes for that project, generates the final docs(<project>/<scope>): <summary> commit subject internally, and no longer treats unrelated pending changes from other projects as an automatic error. Core logic, CLI and MCP inputs, tool descriptions, and tests all reflect the new project-scoped generated-subject contract.

## Provenance

- ad-hoc: Planned after deciding that managed commits must work in a shared multi-project memory repository without rejecting unrelated pending changes, and after refining the API so the tool generates the commit subject from the selected project and inferred scope rather than requiring a redundant caller-supplied full message.

## Dependencies

- none

## Context

- decision:project-memory:2026-03-21:project-scoped-managed-commit-summary-input

## Verification

- Verify commit_pending_changes succeeds when multiple projects have pending managed changes and a target project is provided.
- Verify the commit includes only managed-document paths for the selected project.
- Verify commit_pending_changes rejects a selected project with no pending managed-document changes.
- Verify commit_pending_changes generates docs(<project>/<scope>): <summary> from the selected project, inferred scope, and provided summary.
- Verify CLI and MCP parsing, schemas, and descriptions expose project and summary inputs and no longer require a caller-supplied full commit message.
- Verify legacy tests that enforced the old multi-project rejection or full-message contract are removed or replaced with project-scoped generated-subject behavior checks.

## Evidence

- session-note:project-memory:2026-03-21:implement-project-scoped-managed-commit
- verification-result:project-memory:2026-03-21:implement-project-scoped-managed-commit
