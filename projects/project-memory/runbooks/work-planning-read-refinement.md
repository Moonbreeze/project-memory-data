---
date: 2026-03-14
project: project-memory
topic: work-planning-read-refinement
source: agent
status: archived
---
# Runbook

## Purpose

Refine the planning-side read behavior so future backlog entrypoints can prioritize executable work instead of returning a flat open-item list.

## Procedure

- When reading the backlog for planning, start from open and in-progress work items plus their dependency metadata, not from all active project documents.
- Classify work items into ready, blocked, in-progress, and recently completed slices. Ready means open with no unresolved dependencies; blocked means open with at least one incomplete dependency.
- Read the originating decision only for the work items that are candidates for the next execution slice rather than for the entire backlog at once.
- Expand from a selected work item to its linked canonical docs, recent session notes, and verification evidence only when those documents are needed to execute or validate that slice.
- If several work items share a decision but are dependency-independent, treat them as parallel options rather than as an implied ordered bundle.
- When blocked work dominates a scope, inspect the unmet dependencies first instead of scanning every related document in that scope.

## Verification

- Planning reads can surface the next executable slice without scanning the entire backlog narrative.
- Dependency-independent work from the same decision is preserved as parallel planning options.
- Blocked work leads the reader toward the specific prerequisite items that must be resolved.
- The refinement keeps read expansion narrow and demand-driven even when one decision fans out into several work items.
