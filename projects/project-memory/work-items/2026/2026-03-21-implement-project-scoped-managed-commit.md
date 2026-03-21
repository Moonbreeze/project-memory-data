---
date: 2026-03-21
recorded_at: 2026-03-21T00:00:00.000Z
project: project-memory
topic: implement-project-scoped-managed-commit
source: agent
status: active
work_item_state: open
---
# Work Item

## Summary

Implement project-scoped managed commits and remove the old multi-project pending-tree rejection contract.

## Outcome

The project-memory commit flow accepts an explicit project selector, commits only pending managed-document changes for that project, and no longer treats unrelated pending changes from other projects as an automatic error. Core logic, CLI and MCP inputs, tool descriptions, and tests all reflect the new project-scoped contract.

## Provenance

- ad-hoc: Planned after deciding that managed commits must work in a shared multi-project memory repository without rejecting unrelated pending changes from other projects.

## Dependencies

- none

## Context

- decision:project-memory:2026-03-21:project-scoped-managed-commit-selection

## Verification

- Verify commit_pending_changes succeeds when multiple projects have pending managed changes and a target project is provided.
- Verify the commit includes only managed-document paths for the selected project.
- Verify commit_pending_changes rejects a selected project with no pending managed-document changes.
- Verify the commit message project must match the explicitly selected project.
- Verify CLI and MCP parsing, schemas, and descriptions expose the project selector and no longer describe multi-project pending trees as an automatic error.
- Verify legacy tests that enforced the old multi-project rejection are removed or replaced with project-scoped behavior checks.

## Evidence

- none
