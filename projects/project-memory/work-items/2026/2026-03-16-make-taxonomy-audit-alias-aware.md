---
date: 2026-03-16
project: project-memory
topic: make-taxonomy-audit-alias-aware
source: user
status: active
work_item_state: done
---
# Work Item

## Summary

Make taxonomy audit semantics alias-aware so audit and authority-model behavior do not diverge.

## Outcome

Project-memory defines and implements how taxonomy aliases participate in canonical-doc audit checks, with tests that align audit results to the taxonomy authority model.

## Provenance

- ad-hoc: Follow-up after reviewing the first taxonomy governance implementation and identifying that audit semantics do not yet account for taxonomy aliases.

## Dependencies

- none

## Context

- decision:project-memory:2026-03-15:taxonomy-registry-authority-model
- decision:project-memory:2026-03-15:taxonomy-governance-enforcement-and-surfaces

## Verification

- Decide whether canonical-doc usage of an alias should be treated as valid, warning-level transitional behavior, or an error, and capture that contract explicitly in tests.
- Add automated coverage for canonical docs that target alias-backed names so audit behavior is deterministic and explainable.
- Ensure alias-related audit behavior does not silently diverge from the taxonomy authority model or create false duplicate-authority / unknown-scope outcomes.
- If the implementation changes stable current-truth guidance for taxonomy audit semantics, update the relevant canonical guidance rather than leaving the rule implicit in code and tests only.

## Evidence

- verification-result:project-memory:2026-03-16:make-taxonomy-audit-alias-aware
- session-note:project-memory:2026-03-16:make-taxonomy-audit-alias-aware
