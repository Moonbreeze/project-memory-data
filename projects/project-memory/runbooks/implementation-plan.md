---
date: 2026-03-11
project: project-memory
topic: implementation-plan
source: imported
status: active
---

# Project Memory Implementation Plan

This runbook is the canonical in-repository implementation plan for `project-memory`.
It was moved from the repository root into the structured project-memory tree so it follows the same storage rules it defines.

## Goal

Build a private, multi-project knowledge base for AI agents that stays outside the main repository history and can be read and updated through a narrow MCP surface.

## Principles

- Keep private operational knowledge out of the public repository history.
- Treat this as structured project memory, not a free-form notes dump.
- Use `project-memory` as the canonical project-memory store for all agents, including Claude.
- Allow agents to write only through constrained operations.
- Prevent secrets, raw `.env` data, and sensitive logs from being stored.
- Keep archived material outside the active project tree so agents do not treat it as working context by default.
- Prefer local commits first; do not require automatic push in the first version.
- Assume a single primary operator for MVP; concurrent writes are a known limitation.

## Target Outcome

A private repository named `project-memory` contains:

- structured project-scoped documents under `projects/<project>/`
- archived documents under `archives/<project>/`
- a shared Node.js/TypeScript core for validation, document operations, search, git, and archive handling
- a narrow MCP server that exposes approved document operations
- an optional thin CLI/shell layer for bootstrap, commit, archive, and manual debugging

The system lets agents:

- list and search active private project documents
- read individual documents
- append session notes
- record verification results
- update provider notes and decisions
- commit pending private-doc changes
- manually archive stale documents

## Current Status

The current repository implements the MVP surface in one repository:

- shared Node.js/TypeScript core under `src/core/`
- narrow MCP surface under `src/mcp/`
- CLI wrappers under `src/cli/` and `scripts/`
- document validation for secret-like content, `.env`-style lines, raw dumps, and path restrictions
- archive support for session notes and verification results
- commit scope enforcement for `session`, `verification`, `provider`, `decision`, `runbook`, `archive`, and `mixed`
- passing automated verification with `npm test` and `npx tsc --noEmit`

This is good enough for MVP behavior and safety boundaries, but it is not yet the target repository split.
The codebase and the private memory data still live in the same repository, which blocks making the tool repository public without carrying private-memory structure alongside it.

## Next Iteration

The next iteration should treat repository separation as the primary task, not as a follow-up cleanup.

Target state for that iteration:

- a public tool repository contains code, templates, tests, and generic documentation
- a private memory repository contains only `projects/`, `archives/`, and installation-specific operational documents
- the shared core resolves a `toolRoot` separately from `memoryRoot`
- CLI, MCP, bootstrap, and tests operate correctly when tool code and private memory live in different repositories

Non-goal for that iteration:

- do not add new user-facing document operations before the repository split is complete

## Phase 1: Scope And Boundaries

1. Define what belongs in `project-memory`:
   - session notes
   - live verification results
   - runbooks
   - provider quirks
   - internal decisions
2. Define what must never be stored:
   - tokens and secrets
   - raw `.env` content
   - customer/user-sensitive data
   - unfiltered command output that may contain secrets
   - bulk logs or dumps copied without review
3. Write these rules into a top-level policy document.
4. Document system boundaries:
   - `project-memory` is the canonical store for project memory across agents
   - agent-specific memory systems may exist, but are not the primary store for these artifacts

## Phase 2: Repository Structure

Create this initial layout:

```text
project-memory/
  README.md
  MEMORY_POLICY.md
  AGENT_RULES.md
  package.json
  package-lock.json
  tsconfig.json
  src/
    core/
      config/
      documents/
      validation/
      search/
      git/
      archive/
      types/
    mcp/
      server.ts
      tools/
    cli/
      index.ts
      commands/
  templates/
    session-note.md
    verification-result.md
    provider-note.md
    decision.md
    runbook.md
  projects/
    <project-slug>/
      decisions/
        YYYY/
      provider-notes/
      runbooks/
      session-log/
        YYYY/
          MM/
      verification/
        YYYY/
  archives/
    <project-slug>/
      session-log/
        YYYY/
          MM/
      verification/
        YYYY/
  scripts/
    bootstrap.sh
    docs-commit.sh
    docs-archive.sh
  tests/
    core/
    mcp/
    cli/
    fixtures/
```

Suggested file conventions:

- `projects/<project>/decisions/YYYY/YYYY-MM-DD-short-title.md`
- `projects/<project>/provider-notes/<provider>.md`
- `projects/<project>/runbooks/<topic>.md`
- `projects/<project>/verification/YYYY/YYYY-MM-DD-<topic>.md`
- `projects/<project>/session-log/YYYY/MM/YYYY-MM-DD-<topic>.md`
- `archives/<project>/session-log/YYYY/MM/YYYY-MM-DD-<topic>.md`
- `archives/<project>/verification/YYYY/YYYY-MM-DD-<topic>.md`

Project identifiers should use `kebab-case`.

## Phase 3: Document Format

Use Markdown with small YAML frontmatter.

Required frontmatter fields by default:

- `date`
- `project`
- `topic`
- `source`
- `status`

Optional frontmatter fields by default:

- `project_commit`

Constrain metadata values:

- `source` should be a fixed enum such as `agent`, `user`, `manual`, `tool`, `imported`
- `status` should be a fixed enum such as `draft`, `active`, `superseded`, `archived`

Create templates for:

- session note
- verification result
- provider note
- architectural/operational decision
- runbook

## Phase 4: Shared Core And Adapters

Implement one shared core in `src/core/` and expose it through thin adapters.

Core modules should stay isolated and narrowly scoped rather than collapsing into one service layer.
Prefer explicit boundaries and one-way dependencies between modules.

Suggested module boundaries:

- `config/`: repository roots, project resolution rules, allowed document types, frontmatter enums/defaults, size limits, archive policy defaults
- `documents/`: document-type contracts, path resolution, template rendering, metadata normalization
- `validation/`: schema validation, secret heuristics, raw-dump rejection
- `search/`: active-document listing and full-text search
- `git/`: staging and commit operations limited to approved paths
- `archive/`: archive target resolution and move operations
- `types/`: shared TypeScript types and DTOs

Core responsibilities across those modules:

- resolve approved paths from `project` and document type
- load and render templates
- normalize and validate metadata
- enforce allowed write targets
- search active documents
- stage and commit approved changes
- move documents into archive paths

Adapters:

- MCP server in `src/mcp/`
- optional CLI in `src/cli/`
- thin shell wrappers in `scripts/` only where convenient for local operations

Initial user-facing commands or equivalents:

- `append_session_note`
- `record_verification_result`
- `upsert_provider_note`
- `create_decision`
- `search_documents`
- `commit_pending_changes`
- `archive_documents`

Requirements:

- write only to approved directories
- fill templates automatically
- normalize metadata fields
- fail on invalid or incomplete input
- keep business logic out of bash wrappers

## Phase 5: Validation And Sanitization

Before writing any document:

1. Validate against a document schema and allowed document structure.
2. Accept only approved metadata fields and body sections for each document type.
3. Check for token-like patterns.
4. Reject obvious `.env`-style secret lines.
5. Reject raw dumps and unreviewed command output.
6. Reject oversized entries.
7. Optionally redact dangerous values in tightly scoped cases.
8. Ensure required metadata fields are present.

Create one validation module used by all write operations.

## Phase 6: MCP Server

Expose a narrow MCP surface backed directly by the shared core.

Recommended methods:

- `list_documents`
- `search_documents`
- `read_document`
- `append_session_note`
- `record_verification_result`
- `upsert_provider_note`
- `create_decision`
- `commit_pending_changes`

Do not expose unrestricted shell or unrestricted git write access.

Default MCP behavior should operate only on active documents under `projects/`.
Archives under `archives/` should not be part of normal list or search operations.
`archive_documents` should stay out of the MVP MCP surface and remain a manual CLI-driven operation.

## Phase 7: CLI And Shell Helpers

Provide a minimal manual interface for local operations and debugging.

Recommended commands:

- `docs-bootstrap`
- `docs-commit`
- `docs-archive`
- `docs-create-decision`

Shell scripts in `scripts/` should be thin wrappers around the Node.js entry points.

## Phase 8: Git Workflow

1. Initialize `project-memory` as a private git repository.
2. Treat repository bootstrap as a separate step from normal commits.
3. Commit through shared-core or CLI flows with scripted message formats.
4. Use predictable commit message formats, for example:
   - `docs(session): codex resume verification`
   - `docs(provider): claude approval note`
   - `docs(decision): private docs boundary`
   - `docs(archive): acme-app session-log 2025-12`
   - `docs(mixed): archive stale notes and add follow-up decision`
5. `archive` scope should be used only when pending changes are archive-only moves.
6. If archive paths and active project documents are committed together, require `docs(mixed): ...`.
7. `commit_pending_changes` should stage only approved paths inside `project-memory`.
8. Keep push separate from commit in the initial version.

## Phase 9: Agent Rules

Document operating rules for agents:

- read before writing when relevant
- use `project-memory` as the shared project-memory system across agents
- write only through MCP methods or approved local wrappers
- do not store secrets or raw credentials
- do not rewrite large sections of history without explicit instruction
- prefer append or targeted update patterns over broad edits
- treat archives as non-working context unless explicitly requested

Known limitation for MVP:

- concurrent writes are not resolved automatically
- assume one primary operator
- if multiple agents are involved, assign one agent responsibility for project-memory updates

Document update semantics for MVP:

- `provider note` is a structured living document with one file per provider
- `upsert_provider_note` should overwrite only managed sections from structured input, not perform free-form merge
- `decision` is an immutable record by default
- create new decision files instead of updating old ones, except for tightly scoped status changes if such a flow is added later

## Phase 10: MVP Verification

Verify these scenarios:

1. Create a session note in `projects/<project>/session-log/...`.
2. Record a verification result in `projects/<project>/verification/...`.
3. Update a provider note in `projects/<project>/provider-notes/...`.
4. Search and read active stored documents.
5. Reject a note containing a secret-like string.
6. Reject a note containing raw `.env`-style content.
7. Commit pending changes successfully.
8. Archive selected stale documents into `archives/<project>/...`.
9. Confirm archive files are excluded from default MCP list and search operations.
10. Confirm no unrestricted write path exists outside the allowed structure.

Testing strategy for MVP:

- unit tests for path resolution, metadata normalization, validation, and archive path mapping
- integration tests for MCP read/write flow, `commit_pending_changes`, and exclusion of `archives/` from default list/search behavior

## Phase 11: Future Extensions

Possible later additions:

- optional push/pull helpers
- archive restore flows
- document indexing
- cross-reference generation
- review queue for agent-written notes
- sync into a separate backup remote
- conflict detection or optimistic locking
- import or migration helpers from agent-specific memory stores

## Recommended First Implementation Session

1. Scaffold repository structure and Node.js/TypeScript project files.
2. Add policy documents, agent rules, and templates.
3. Implement core path resolution and document types.
4. Implement validation and sanitization.
5. Implement two write operations first:
   - `append_session_note`
   - `record_verification_result`
6. Add `search_documents` and `commit_pending_changes`.
7. Add manual archive support.
8. Wrap the core with the MCP server.
9. Add the minimal CLI and shell wrappers.
10. Test the full flow end-to-end.

## Suggested Definition Of Done

The MVP is done when:

- agents can read and write structured private notes through MCP
- `project-memory` works as the canonical project-memory store across agents
- writes are limited to approved document types and approved project paths
- secret-like content and raw dumps are blocked
- archives are separated from active working context
- changes can be committed locally with consistent metadata
- the system is usable as persistent project memory across sessions and projects
