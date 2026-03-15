---
date: 2026-03-14
project: project-memory
topic: core-user-scenarios-baseline
source: agent
status: archived
---
# Runbook

## Purpose

Capture the first compact set of user-facing scenarios that should drive canonical-doc and future work-item design, so later implementation sessions can scope behavior against concrete flows instead of abstract feature lists.

## Procedure

- Scenario 1, maintain canonical project documentation: trigger when a project topic needs a living source of truth or existing repository docs must be replaced; flow is identify the topic and ownership boundary, create or update exactly one canonical document for that topic, link the governing decision when relevant, review for secrets and stale operational detail, then treat that canonical document as the current project reference.
- Scenario 2, derive executable work from a decision or follow-up: trigger when an active decision implies unfinished implementation or a session note records remaining work; flow is capture one work item that references the originating decision or note, define expected outcome and verification target, and place it into the operational backlog without changing the decision lifecycle.
- Scenario 3, complete a work item with evidence: trigger when implementation work is finished; flow is update the work item to done, append a session note describing the actual actions taken, record verification results for the promised checks, and update related canonical docs if system behavior or process changed.
- Scenario 4, supersede a decision: trigger when a newer architectural conclusion replaces an older one; flow is create the new decision with explicit replacement context, change the older decision to superseded rather than silently editing history, and update linked canonical docs or work items to point at the current decision.
- Scenario 5, migrate repository documentation into project-memory: trigger when a project wants project-memory to become the canonical home for selected private docs; flow is declare project policy first, import or rewrite the source material into canonical documents, leave a minimal repository bootstrap note if needed, and only then remove or shrink repository-local docs.
- Scenario 6, review backlog and plan next session: trigger at session start or after major work lands; flow is inspect open work items and their linked decisions or docs, identify blocked versus ready work, choose the next implementation slice, and avoid treating active decisions themselves as closeable backlog entries.

## Verification

- Each scenario identifies a trigger, participating document roles, and the expected write operations or transitions.
- The scenario set separates decision semantics from executable work and from canonical documentation maintenance.
- Canonical-doc requirements and work-item requirements can be mapped back to at least one explicit scenario.
- The scenario inventory is compact enough to guide several follow-up sessions without becoming a second unstructured backlog.
