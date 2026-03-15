---
date: 2026-03-15
project: project-memory
topic: retire-registered-topic
source: user
status: active
---
# Runbook

## Purpose

Remove one registered topic from active taxonomy use while preserving correct historical interpretation and authority transitions.

## Procedure

- Confirm the topic should leave active taxonomy use and determine whether it is superseded by another topic, kept only for historical lookup, or removed without replacement.
- Update the taxonomy registry so the retired topic records its lifecycle outcome and any successor or historical-only handling explicitly.
- Inspect active canonical documents for the retired topic and archive, supersede, or migrate them according to the recorded retirement outcome.
- Review aliases and references so they do not continue to present the retired topic as an active authority surface.
- Run a taxonomy audit after retirement to verify that no active write path or active canonical document still depends on the retired topic as authoritative.
- Record the retirement rationale clearly enough that later audits can distinguish intentional retirement from accidental taxonomy loss.

## Verification

- Confirm the retirement reason and replacement or non-replacement status are explicit in the registry.
- Confirm active canonical documents were archived, superseded, or migrated appropriately.
- Confirm aliases and references no longer present the retired topic as an active authority surface.
- Confirm no active authority write path still targets the retired topic unless the registry explicitly marks it transitional.
