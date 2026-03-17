---
date: 2026-03-15
recorded_at: 2026-03-15T00:00:00.000Z
project: project-memory
topic: strengthen-decision-and-canonical-doc-process
source: agent
status: active
work_item_state: open
---
# Work Item

## Summary

Define stronger process guardrails between decisions and canonical docs to reduce contradictions and ownership blur; this item remains the umbrella for the broader topic while narrower implementation slices may be tracked separately.

## Outcome

Project-memory has explicit rules for how new decisions relate to prior decisions and when canonical docs must be updated so operational guidance stays consistent. This item remains the umbrella for the broader process topic, while focused implementation follow-ups such as `implement-decision-write-guidance-review-contract` are tracked separately.

## Provenance

- ad-hoc: Architecture review identified process fragility around repeated decisions on the same topic and unclear handoff between immutable rationale and mutable current-truth guidance.

## Dependencies

- none

## Context

- none

## Verification

- Document the intended responsibility split between decision and canonical-doc.
- Identify failure modes such as duplicate active decisions on one topic or stale canonical docs after a new decision.
- Define when an accepted and implemented decision should trigger a review of existing canonical guidance, even when no new canonical doc is obviously required during implementation.
- Define the expected outcomes of that review, such as no change, update canonical-doc, create canonical-doc, or supersede/archive outdated guidance.
- Use the recently implemented taxonomy governance decisions as a pilot case for this post-decision/post-implementation review trigger and its expected outcomes.
- Propose targeted process or tool guardrails that reduce contradiction risk without making the write flow unusably heavy.
- Keep the decision-side implementation slice tracked separately in work-item:project-memory:2026-03-17:implement-decision-write-guidance-review-contract rather than collapsing this umbrella item into a single implementation contract.

## Evidence

- none
