---
date: 2026-03-17
recorded_at: 2026-03-17T00:00:00.000Z
project: project-memory
topic: implement-decision-write-guidance-review-contract
source: agent
status: active
work_item_state: done
---
# Work Item

## Summary

Implement the decision-side contract that requires an explicit stable-guidance review outcome for non-draft decision writes without depending on work-item completion.

## Outcome

Project-memory has a concrete implementation slice for enforcing or surfacing stable-guidance review at create_decision time, including explicit treatment for draft and bootstrap cases and verification of decision immutability or overwrite behavior.

## Provenance

- ad-hoc: Follow-up after evaluating whether stable-guidance review should be enforced at work-item completion or directly on decision writes; the chosen next slice is to design and implement the contract on create_decision instead of work-item closure.

## Dependencies

- none

## Context

- none

## Verification

- Define the intended create_decision contract for stable-guidance review on non-draft decision writes.
- Decide how draft decisions and bootstrap-style decision writes are handled so the rule does not require phantom work-items.
- Determine whether the contract should be descriptive-only, validated through structured inputs, or enforced through tool behavior.
- Verify whether existing decisions can be overwritten by path reuse and document the required immutability or supersession guardrail.
- Confirm the final implementation path keeps project-memory self-contained rather than depending on ai-inst modules for primary correctness.

## Evidence

- verification-result:project-memory:2026-03-17:implement-decision-write-guidance-review-contract
- session-note:project-memory:2026-03-17:implement-decision-write-guidance-review-contract
