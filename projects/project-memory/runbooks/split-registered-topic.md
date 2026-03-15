---
date: 2026-03-15
project: project-memory
topic: split-registered-topic
source: user
status: active
---
# Runbook

## Purpose

Replace one overly broad registered topic with multiple narrower topics when one authority surface no longer models the space cleanly.

## Procedure

- Confirm the current topic is too broad for one semantic unit or one authority boundary and that the operation is not merely a rename.
- Define the successor topics, their scopes, and their authority boundaries explicitly before modifying active authority surfaces.
- Update the taxonomy registry so the successor topics are registered and the predecessor topic records its successor relationship and lifecycle transition.
- Review existing canonical documents that point at the predecessor topic and decide which documents move to successor topics, which are superseded, and which require new canonical surfaces.
- Adjust aliases and references so historical lookups remain understandable without masking the fact that the old topic was actually split.
- Run a taxonomy audit after the split so no active canonical document still depends on the predecessor topic as if it remained authoritative.

## Verification

- Confirm the original topic was intentionally split into explicit successor topics.
- Confirm successor scopes and authority boundaries are recorded in the registry.
- Confirm dependent canonical documents were updated, superseded, or replaced intentionally.
- Confirm historical lineage from predecessor to successors remains traceable and no active authority still depends on the retired broad topic.
