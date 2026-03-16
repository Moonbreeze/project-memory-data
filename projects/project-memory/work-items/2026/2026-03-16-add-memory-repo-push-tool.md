---
date: 2026-03-16
project: project-memory
topic: add-memory-repo-push-tool
source: agent
status: active
work_item_state: done
---
# Work Item

## Summary

Add a separate lifecycle tool that pushes committed memory-repo changes to a remote without changing the local-only commit helper contract.

## Outcome

Project-memory provides an explicit post-commit push step for the managed memory repository, with validated remote/branch handling and updated lifecycle guidance.

## Provenance

- ad-hoc: User requested a separate push tool instead of extending commit_pending_changes with implicit origin push behavior.

## Dependencies

- none

## Context

- none

## Verification

- Define the push tool contract so it does not silently change commit_pending_changes semantics.
- Implement CLI and MCP support for pushing the current memory-repo branch to a remote with sensible defaults and clear failure behavior.
- Add automated coverage for successful push flow and basic remote/configuration errors.
- Update lifecycle guidance so the documentation flow reflects commit followed by explicit push when desired.

## Evidence

- session-note:project-memory:2026-03-16:add-memory-repo-push-tool
- verification-result:project-memory:2026-03-16:add-memory-repo-push-tool
