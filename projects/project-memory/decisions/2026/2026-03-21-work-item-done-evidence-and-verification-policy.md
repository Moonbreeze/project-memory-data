---
date: 2026-03-21
recorded_at: 2026-03-21T00:00:00.000Z
project: project-memory
topic: work-item-done-evidence-and-verification-policy
source: agent
status: active
---
# Decision

## Context

The current work-item model allows session-note and verification-result locators in evidence, but closing a work-item to done does not require either one. That leaves room for agents to mark execution complete without any recorded chronology, and the recommendation layer does not state clearly enough when evidence must be added before close_work_item. At the same time, requiring an automatic test-specific gate for every code-related slice would overfit the model because verification-result is intentionally broader than automated tests and the current schema does not encode a machine-checkable code-work flag.

## Decision

Require the work-item done state to have at least one session-note locator recorded in evidence as a hard model invariant, and update MCP-facing guidance to state that when a work-item included code changes, agents should record a verification-result describing the checks that actually ran before treating the slice as done. Do not add a separate hard invariant for code-work verification until the model carries an explicit machine-checkable signal for that distinction.

## Consequences

- Agents can no longer close a work-item to done without at least one recorded execution chronology artifact linked through evidence.
- The authoritative closure flow becomes clearer: append or identify the session-note, update work-item evidence, then close the work-item, with archive remaining a separate later step.
- Verification guidance for code-work slices becomes explicit without incorrectly forcing every valid check into an automated-test-only shape.
- Any future hard enforcement for verification on code-work slices will require a deliberate schema change rather than hidden heuristics in close_work_item.

## Stable Guidance Review

- Outcome: reviewed-no-change
- Summary: Reviewed current stable guidance and determined no update was required.
