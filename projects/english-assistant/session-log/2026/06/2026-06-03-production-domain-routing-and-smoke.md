---
date: 2026-06-03
recorded_at: 2026-06-03T10:14:08.263Z
project: english-assistant
topic: production-domain-routing-and-smoke
source: agent
status: active
---
# Session Note

## Summary

Completed the repo-side production domain routing work by adding a versioned reverse proxy config, a testable routing contract, and a local smoke runner for the landing/app hostname split.

## Actions

- Added `deploy/reverse-proxy/Caddyfile` with root, `www`, and `assistant` hostname handling for the landing/app split.
- Added `deploy/reverseProxyRouting.ts` and `deploy/reverseProxySmoke.ts` plus tests to validate the routing contract locally.
- Extracted landing CTA host resolution into `packages/landing/src/assistantUrl.ts` and covered root/`www`/assistant host behavior with tests.

## Follow-up

- Apply the versioned reverse proxy config on the production VPS and wire `ROOT_DOMAIN`, `LANDING_UPSTREAM`, and `APP_UPSTREAM` in the running Caddy service.
- Run public production smoke checks for root-domain, `www` redirect, `assistant` subdomain, and CTA navigation after deploy.
