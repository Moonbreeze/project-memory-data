---
date: 2026-03-14
project: project-memory
topic: project-scoped-doc-commit-protocol
source: agent
status: active
---
# Runbook

## Purpose

Define the managed-doc commit protocol for `project-memory-data` so commit history stays readable by project and scope, and so later automation can commit document writes without mixing unrelated projects.

## Procedure

- Use the commit message format `docs(<project>/<scope>): <summary>` for managed-doc commits in `project-memory-data`.
- Infer `<project>` from the changed managed-document paths and require that the default commit batch stays within one project.
- Infer `<scope>` from the changed document types when possible, and fall back to `mixed` when a single logical batch includes multiple managed document types for the same project.
- Treat cross-project batches as exceptional: do not use them in the default flow, and require an explicit separate path if they are ever supported later.
- When implementing automatic commits in `project-memory`, align the commit unit with one managed write operation or one explicit logical batch rather than with the entire dirty worktree.
- Keep project-aware validation in the tool so commit messages and staged path sets stay consistent.

## Verification

- A reader can identify the target project directly from the commit message without opening the diff.
- The default protocol prevents unrelated projects from being committed together by accident.
- The protocol is specific enough to implement later as project-aware commit parsing, validation, and automatic commit inference inside `project-memory`.
