---
date: 2026-03-15
project: project-memory
topic: rename-registered-topic-and-preserve-aliases
source: user
status: active
---
# Runbook

## Purpose

Rename one registered topic when the semantic unit and authority boundary stay the same but the canonical label should change.

## Procedure

- Confirm the proposed new label denotes the same semantic unit and authority boundary as the current base topic and that the change is not really a split, merge, or boundary change.
- Resolve the active taxonomy registry and update the affected entry so the new label becomes the base topic.
- Retain the former base topic as an alias unless there is a deliberate reason to remove historical lookup compatibility.
- Review references, lookups, and dependent guidance surfaces so they continue to resolve through the renamed topic.
- Check for accidental duplicate registrations created by the rename and remove or reconcile them before finishing.
- Record the rename rationale clearly enough that later audits can distinguish a true rename from a semantic restructuring.

## Verification

- Confirm the semantic boundary did not change during the rename.
- Confirm the new label is the base topic and the former base label remains available as an alias when continuity is required.
- Confirm dependent references still resolve correctly after the rename.
- Confirm no duplicate active registered topic remains for the same semantic unit.
