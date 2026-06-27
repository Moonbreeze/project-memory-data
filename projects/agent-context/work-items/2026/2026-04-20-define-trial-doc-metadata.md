---
date: 2026-04-20
recorded_at: 2026-04-20T13:20:50.564Z
project: agent-context
topic: define-trial-doc-metadata
source: agent
status: active
work_item_state: done
---
# Work Item

## Summary

Define metadata conventions for authoring documents that may later be extracted into ai-inst modules or skills.

## Outcome

Authoring sources in agent-context make their role, maturity, and intended extraction target explicit.

## Provenance

- ad-hoc: Initial implementation planning for the agent-context MVP, now reframed around the authoring-repo and project-memory split.

## Dependencies

- work-item:agent-context:2026-04-20:scaffold-agent-context-structure

## Context

- canonical-doc:agent-context:2026-06-21:documentation-model
- canonical-doc:agent-context:2026-06-21:trial-mode
- decision:agent-context:2026-06-21:authoring-repo-project-memory-split

## Verification

- Define a shared metadata or frontmatter format for new authoring documents.
- Make authoring sources distinguishable from project-memory runtime records by role and authority.
- Record the intended extraction target when a document is meant to become a module, skill, template, or other behavior artifact.

## Evidence

- session-note:agent-context:2026-06-27:define-trial-doc-metadata
- verification-result:agent-context:2026-06-27:define-trial-doc-metadata
