---
date: 2026-03-14
project: project-memory
topic: document-lifecycle-graph-baseline
source: agent
status: active
---
# Runbook

## Purpose

Record the baseline lifecycle model for the core project-memory document roles before canonical-doc and work-item support are implemented in code.

## Procedure

- Decision lifecycle graph: draft -> active -> superseded or archived. Active means the decision is currently valid; superseded means replaced by a newer decision; archived means removed from the active body of records without implying replacement. Implementation completion alone must not cause an active decision to leave that state.
- Canonical-doc target lifecycle graph: draft -> active -> superseded or archived. Active means this is the living source of truth for one topic; superseded means replaced by a newer canonical doc for the same topic or scope; archived means intentionally removed from active reference use. The model should prefer one active canonical doc per topic.
- Work-item target lifecycle graph: open -> in_progress -> done, with side paths to blocked or canceled. Work items represent executable backlog units, not long-lived architectural truth. Done work items may remain readable for traceability but should no longer drive active planning views.
- Session-note lifecycle graph: active while it remains part of the recent working record, then archived when moved out of the active project tree. Session notes describe what happened, not what is currently true or still required.
- Verification-result lifecycle graph: active while it belongs in the current working set, then archived when it becomes historical evidence. Verification results support confidence and traceability but are not themselves backlog items or canonical behavior descriptions.
- Relationship graph baseline: decisions govern canonical docs and can spawn work items; work items produce session notes and verification results; canonical docs may be updated as a consequence of completed work; superseding a decision or canonical doc should update forward links without deleting prior records.

## Verification

- The lifecycle model gives each document role a distinct meaning and avoids overloading decision status for task completion.
- The baseline graph supports the upcoming canonical-doc feature without forcing canonical content into runbook or decision templates.
- The future work-item lifecycle is specific enough to design backlog views and close-state operations later.
- Cross-document relationships are explicit enough to split implementation into document type, lifecycle operation, and agent workflow sessions.
