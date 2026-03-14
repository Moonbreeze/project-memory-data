---
date: 2026-03-14
project: project-memory
topic: scenario-and-lifecycle-baseline
source: agent
status: active
---
# Session Note

## Summary

Created the first scenario and lifecycle baseline for the upcoming canonical-doc and work-item evolution. The artifacts separate valid decisions from executable work, outline the main user flows, and define a target lifecycle model for future implementation slices.

## Actions

- Created a runbook that captures six core user scenarios covering canonical-doc maintenance, work derivation, work completion with evidence, decision supersession, repo-doc migration, and backlog review.
- Created a runbook that defines the baseline lifecycle graphs for decisions, canonical docs, work items, session notes, verification results, and their cross-document relationships.
- Anchored the next implementation phase around scenario-driven and lifecycle-driven design rather than around standalone tool or rule additions.

## Follow-up

- Translate the baseline scenarios into concrete canonical-doc requirements: path layout, update semantics, validation profile, and read/list/search behavior.
- Define the minimum work-item schema and lifecycle operations needed to replace the current active-decision backlog shortcut.
- Decide which agent-facing rules belong in project-specific instructions only after the canonical-doc and work-item workflows are stable enough to describe precisely.
