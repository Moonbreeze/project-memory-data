---
date: 2026-03-21
recorded_at: 2026-03-21T00:00:00.000Z
project: project-memory
topic: project-scoped-managed-commit-summary-input
source: agent
status: active
---
# Decision

## Context

The new project-scoped commit direction removed the old multi-project pending-tree rejection, but the current planned contract still expects users to pass a full commit message in docs(<project>/<scope>): <summary> format. Once commit_pending_changes already receives an explicit target project and derives scope from the selected pending managed-document set, requiring the caller to repeat the project inside the commit message becomes redundant and creates a second source of truth that can drift from the selected project.

## Decision

Adopt a generated commit-subject contract for project-scoped managed commits. commit_pending_changes must accept an explicit project selector plus a free-text summary, derive the managed-doc scope from the selected pending changes for that project, and construct the final git commit subject internally as docs(<project>/<scope>): <summary>. The tool must no longer require callers to supply the full prefixed commit message manually.

## Consequences

- The commit API becomes simpler and less error-prone because callers provide only the target project and human-written summary, while the tool owns the deterministic docs(<project>/<scope>): prefix.
- Validation shifts from checking whether a user-supplied commit message project matches the selected project to checking that the selected project has pending managed-document changes and that the provided summary is valid for a git commit subject.
- CLI, MCP parsing, schemas, descriptions, and tests must move from a message field to project plus summary input while still returning the generated commit subject in results for transparency.
- The earlier project-scoped selection decision is superseded because it preserved a redundant user-supplied full-message contract that no longer matches the intended API design.

## Stable Guidance Review

- Outcome: reviewed-no-change
- Summary: Reviewed current stable guidance and determined no update was required.
