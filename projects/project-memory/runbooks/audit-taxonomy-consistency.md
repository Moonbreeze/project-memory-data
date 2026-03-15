---
date: 2026-03-15
project: project-memory
topic: audit-taxonomy-consistency
source: user
status: active
---
# Runbook

## Purpose

Check that the active taxonomy registry, active canonical documents, and reserved registry invariants remain consistent after bootstrap, migration, or any taxonomy change.

## Procedure

- Resolve the active taxonomy registry surface for the target project and verify that exactly one active registry document exists.
- Inspect all active non-registry canonical documents and compare each declared registry scope against the active taxonomy registry.
- Identify duplicate active authority claims for the same scope, canonical documents that target unknown scopes, and registry entries whose lifecycle state no longer matches active document usage.
- Check retired topics to ensure they are not still being used as active authority surfaces and that any stated replacement or historical-only handling is reflected consistently.
- Review aliases for accidental boundary drift so broader or narrower names are not being used where a split, merge, boundary change, or rename is required.
- Produce an audit result that distinguishes pass, conflict, unresolved ambiguity, and required cleanup actions.

## Verification

- Confirm every active non-registry canonical document uses a registered scope in the active taxonomy registry.
- Confirm no duplicate active authority exists for the same scope.
- Confirm no active registry conflicts or unresolved lifecycle mismatches remain hidden in the result.
- Confirm retired topics are not still targeted by active authority surfaces unless the registry explicitly marks them transitional.
