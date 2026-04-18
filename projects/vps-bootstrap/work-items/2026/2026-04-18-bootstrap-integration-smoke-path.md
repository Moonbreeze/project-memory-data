---
date: 2026-04-18
recorded_at: 2026-04-18T15:30:08.814Z
project: vps-bootstrap
topic: bootstrap-integration-smoke-path
source: agent
status: active
work_item_state: open
---
# Work Item

## Summary

Define and implement a higher-fidelity smoke path for validating phased bootstrap execution.

## Outcome

The project has an explicit executable slice for designing and adding a more realistic validation path for phased bootstrap flow, with clear scope and expected result.

## Provenance

- ad-hoc: Follow-up after adding phased bootstrap execution and managed shell-profile provisioning; the repository now needs a more realistic smoke or integration validation path beyond shell-level dry-run tests.

## Dependencies

- none

## Context

- canonical-doc:vps-bootstrap:bootstrap:bootstrap

## Verification

- Decide what the minimal integration or smoke path should validate beyond the current shell-based dry-run tests.
- Document concrete success criteria for validating phased execution across `prepare-system`, `provision-user`, `stage-ssh`, and `finalize-hardening`.
- If implementation work starts, ensure the resulting validation path is runnable and can be referenced from the repository validation workflow.

## Evidence

- none
