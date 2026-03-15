---
date: 2026-03-14
project: project-memory
topic: scenario-and-graph-discovery
source: agent
status: archived
---
# Runbook

## Purpose

Guide the first implementation phase for evolving project-memory from decision-backed backlog handling toward a cleaner model with canonical docs and future work-item support.

## Procedure

- Enumerate the primary user scenarios that the model must support before further document-type expansion. Start with: creating or updating a canonical project doc, creating work from a decision or follow-up, completing work with session-note and verification evidence, superseding a decision, and migrating repository docs into project-memory.
- For each scenario, record the actor goal, trigger, participating document types, write operations, lifecycle transitions, and verification artifacts.
- Draw sequence-style flow diagrams for the scenarios and state-transition diagrams for each relevant document type: decision, canonical-doc, future work-item, session-note, and verification-result.
- Identify where the current implementation or memory conventions do not support the desired flows cleanly, especially where decisions are currently standing in for backlog items.
- From the reviewed scenarios and graphs, extract the concrete requirements for canonical-doc support, the minimum work-item model, and any needed CLI or MCP lifecycle operations.
- Only after the workflow model is stable, derive agent skills and project-specific rules that govern when to create, update, link, supersede, archive, or verify each document type.
- Break the implementation into session-sized tracks and keep each session tied back to the scenario or lifecycle gap it addresses.

## Verification

- A reviewed scenario set exists for the main user-facing documentation and planning workflows.
- Lifecycle diagrams clearly separate valid decisions, canonical truth, executable work, activity logs, and verification evidence.
- Canonical-doc requirements and future work-item requirements are traceable to specific scenarios and not just general intent.
- Future sessions can execute one implementation slice at a time without reopening the model question from scratch.
