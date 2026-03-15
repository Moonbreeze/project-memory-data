---
date: 2026-03-14
project: project-memory
topic: cross-project-helper-guardrails
source: agent
status: draft
---
# Decision

## Context

The planning/read branch is now effectively closed through the bounded same-project planning-topic-entry dependency follow added in Session 14. Cross-project relationships remain intentionally out of default runtime behavior: work-item locators stay same-project, backlog planning is project-scoped, and bounded reads follow only explicit same-project dependency, context, and evidence references. The remaining open question is not whether to widen current flows automatically, but how future explicit cross-project helper surfaces could exist without weakening deterministic same-project behavior or reintroducing broad aggregation by default.

## Decision

If cross-project helpers are introduced, keep them as explicit opt-in helper surfaces rather than as implicit extensions of existing default read flows. Any such helper must require an explicit project list or explicit cross-project locators, stay bounded with fixed caps and deterministic ordering, avoid recursive expansion, and leave same-project planning, backlog, and bounded-read defaults unchanged.

## Consequences

- The current same-project planning and bounded-read behavior remains the default contract and does not gain implicit cross-project follow.
- Future cross-project support is constrained to dedicated helper surfaces such as explicit locator-based reads or bounded multi-project packages, not retrofitted into existing default entrypoints.
- Guardrails for any future implementation are now explicit: opt-in inputs only, fixed per-stage limits, deterministic ordering, no recursive graph walk, and clear result labeling for external-project material.
- Cross-project helpers become a candidate for the next roadmap as a separate track after the planning/read branch, rather than a continuation of the current narrow runtime slice.
