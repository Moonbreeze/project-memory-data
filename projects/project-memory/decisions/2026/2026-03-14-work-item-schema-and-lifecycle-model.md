---
date: 2026-03-14
project: project-memory
topic: work-item-schema-and-lifecycle-model
source: agent
status: active
---
# Decision

## Context

Session 5 needed a minimal work-item model that Session 6 can implement without reopening the document design. The project already decided to separate executable work from decisions, to model dependency explicitly, and to keep bounded read behavior narrow and deterministic. The remaining gap was to define a compatible schema, lifecycle split, provenance rules, and relationship boundaries without prematurely wiring a new document type into list, read, search, backlog, CLI, or MCP flows.

## Decision

Adopt a spec-only work-item model with two separate axes: document status remains `draft`, `active`, or `archived`, while execution progress is represented by a distinct `work_item_state` field with `open`, `in_progress`, `blocked`, `done`, and `canceled`. Work-item relationships must use same-project typed locators for `decision`, `canonical-doc`, `session-note`, `verification-result`, and future `work-item` records. Provenance must allow `decision`, `session-note`, or explicit ad-hoc origin. Dependencies are limited to other work items, context is limited to decision, canonical-doc, or session-note references, and evidence is limited to verification-result or session-note references. The future active path layout is `projects/<project>/work-items/<year>/<date>-<topic>.md`, but the document type is not added to the active managed-document pipeline until Session 6.

## Consequences

- Session 6 can implement work-item documents against a fixed schema and path model instead of re-opening lifecycle and provenance design.
- Planning reads can derive ready versus blocked work from dependency state without overloading document status.
- Cross-project relationship handling remains out of scope for the first work-item rollout; work-item links stay same-project and deterministic.
- Current list, search, read, backlog, CLI, and MCP flows remain stable because the Session 5 output is a spec surface only, not a live document-type rollout.
