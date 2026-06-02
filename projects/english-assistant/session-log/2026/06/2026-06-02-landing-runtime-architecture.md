---
date: 2026-06-02
recorded_at: 2026-06-02T16:58:09.719Z
project: english-assistant
topic: landing-runtime-architecture
source: agent
status: active
---
# Session Note

## Summary

Validated the current deploy/runtime baseline and added repository artifacts that make the future landing/app host split explicit before implementation of the landing package.

## Actions

- Inspected the current compose, Dockerfile, server static routing, and deploy script to confirm that production currently runs as a single `app` service serving both backend and client bundle.
- Updated `deploy/README.md` with the current baseline topology and the target split-host production scheme.
- Added `deploy/reverse-proxy/README.md` to reserve a versioned location for production reverse proxy configuration and define routing ownership rules.

## Follow-up

- Implement `landing-package-scaffold-and-shell` by adding `packages/landing` as a separate static bundle with CTA to `assistant.<root-domain>`.
- Extend compose and deploy flow for a dedicated `landing` service in `multi-service-build-and-deploy-integration`.
- Add concrete reverse proxy config and run final production routing smoke in `production-domain-routing-and-smoke`.
