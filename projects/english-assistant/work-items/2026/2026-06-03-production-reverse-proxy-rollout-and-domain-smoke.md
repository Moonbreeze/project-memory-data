---
date: 2026-06-03
recorded_at: 2026-06-03T10:14:26.838Z
project: english-assistant
topic: production-reverse-proxy-rollout-and-domain-smoke
source: agent
status: active
work_item_state: done
---
# Work Item

## Summary

Apply the production reverse proxy config on the VPS and validate the public landing/app domains after deploy.

## Outcome

The live production setup serves the landing from the root-domain, redirects `www` to the canonical root host, serves the application from `assistant.<root-domain>`, and preserves landing CTA navigation into the app.

## Provenance

- session-note:english-assistant:2026-06-03:production-domain-routing-and-smoke

## Dependencies

- work-item:english-assistant:2026-06-02:production-domain-routing-and-smoke

## Context

- none

## Verification

- The root-domain opens the landing in the live production environment.
- `www.<root-domain>` redirects to the canonical root host with the expected location.
- `assistant.<root-domain>` opens the current application in production.
- The landing CTA opens the assistant application on the production hostname after deploy.

## Evidence

- session-note:english-assistant:2026-06-14:production-reverse-proxy-rollout-and-domain-smoke
- verification-result:english-assistant:2026-06-14:production-reverse-proxy-rollout-and-domain-smoke
