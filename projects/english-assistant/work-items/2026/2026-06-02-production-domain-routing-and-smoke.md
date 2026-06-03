---
date: 2026-06-02
recorded_at: 2026-06-02T16:47:42.716Z
project: english-assistant
topic: production-domain-routing-and-smoke
source: agent
status: active
work_item_state: done
---
# Work Item

## Summary

Finalize the repo-side production domain routing contract for the landing/app split and validate it locally before the external VPS rollout.

## Outcome

The repository contains a versioned reverse proxy config, a testable hostname routing contract, and a local smoke runner that validates root-domain landing, `www` canonical redirect, and `assistant` app routing.

## Provenance

- ad-hoc: Split the landing and app public hostnames so the repository contains the production routing contract and local verification before the VPS rollout.

## Dependencies

- work-item:english-assistant:2026-06-02:multi-service-build-and-deploy-integration

## Context

- none

## Verification

- `pnpm test` stays green after the routing and landing host-resolution changes.
- `pnpm smoke:reverse-proxy` confirms root-domain -> landing, `www` -> canonical redirect, and `assistant.<root-domain>` -> app in the local contract harness.

## Evidence

- session-note:english-assistant:2026-06-03:production-domain-routing-and-smoke
- verification-result:english-assistant:2026-06-03:production-domain-routing-and-smoke
