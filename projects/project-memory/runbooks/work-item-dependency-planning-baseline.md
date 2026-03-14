---
date: 2026-03-14
project: project-memory
topic: work-item-dependency-planning-baseline
source: agent
status: active
---
# Runbook

## Purpose

Capture the baseline planning model for future work-item dependencies so backlog behavior can distinguish parallel work from blocked sequential work.

## Procedure

- Treat the originating decision as a shared rationale source, not as the container for execution order. A single decision may fan out into multiple work items.
- Represent independent branches as separate work items with the same originating decision and no dependency edges between them.
- Represent sequential execution by adding explicit dependency links from a downstream work item to the work item or items that must complete first.
- Derive planning states from both lifecycle status and dependency satisfaction. An open item with unresolved dependencies is blocked even if its lifecycle status has not changed to in-progress.
- Prefer small work items with explicit relationships over one large umbrella item when the implementation contains independently shippable or independently verifiable slices.
- Avoid using dates, list ordering, or narrative wording as the only source of execution order; those may support human explanation but should not replace explicit dependency metadata.

## Verification

- The planning model can distinguish independent work from blocked work without reading long narrative context.
- A single decision can support both parallel and sequential implementation slices.
- The future backlog view has enough structure to surface ready work first.
- Dependency handling is explicit enough to inform future read entrypoints and work-item lifecycle operations.
