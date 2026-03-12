---
date: 2026-03-12
project: project-memory
topic: canonical-project-docs-implementation
source: user
status: active
---
# Runbook

## Purpose

Implement canonical project-document support in project-memory and document the related clarification needed in the ai-inst project-memory rules module.

## Procedure

- Add a new managed document kind for canonical project documentation, such as project-doc or canonical-doc, instead of trying to encode long-lived project docs as decisions or runbooks.
- Define a stable repository layout for canonical docs, for example projects/<project>/docs/<slug>.md or a scoped variant such as projects/<project>/docs/<area>/<slug>.md.
- Extend frontmatter for the new document kind with fields suitable for canonical docs, such as title, doc_kind, optional canonical marker, and optional references to former repository paths or replaced documents.
- Add a dedicated template plus CLI and MCP write support for canonical docs. The write path should support upsert semantics so one topic can have one living canonical document without requiring append-only note workflows.
- Keep the existing safety controls for secrets and env-style content, but relax the body-shape validation for the canonical doc type so real documentation is not forced into runbook or decision section headings.
- Extend list, read, and search flows so canonical docs are first-class results and can be filtered cleanly by type and topic.
- Review lifecycle handling so canonical docs can move between active, superseded, and archived states without abusing session-note archive behavior.
- Update README and any install or onboarding docs so users understand when canonical docs belong in project-memory and when repository-local docs are still appropriate.
- Update the ai-inst project-memory rules module with a short conditional clarification: if a project intends to keep canonical project documentation in project-memory, that must be stated explicitly in the project's own rules. Do not make full doc externalization the default assumption for every project.
- After canonical-doc support exists, define a migration pattern for consumer projects: import current docs into project-memory, keep a minimal repository bootstrap note, then remove detailed private docs from the tool repository only after the project-specific policy is in place.

## Verification

- A project can store, update, read, search, and list one canonical documentation page per topic through project-memory without misusing decisions or runbooks.
- The new canonical doc flow still rejects secrets and .env-style content and does not allow unreviewed raw command dumps.
- Documentation-only projects can reduce repository-local docs to bootstrap stubs after explicit project-level policy is declared.
- The ai-inst project-memory module text makes the project-level policy requirement explicit without forcing it on unrelated projects.
- Automated verification remains green after adding the new document type, path handling, validation, and MCP or CLI surface.
