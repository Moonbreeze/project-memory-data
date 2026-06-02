---
date: 2026-06-02
recorded_at: 2026-06-02T16:58:09.666Z
project: english-assistant
topic: landing-runtime-architecture
source: agent
status: active
---
# Verification Result

## Scope

landing runtime topology and deploy routing contract

## Steps

- Reviewed `docker-compose.yml` and confirmed the current production baseline is a single `app` service.
- Reviewed `Dockerfile` and `packages/server/src/index.ts` to confirm the current app serves both backend routes and the built client bundle.
- Reviewed `deploy/deploy.sh` and `deploy/README.md` to confirm webhook deploy already rebuilds the whole compose project.
- Added `deploy/reverse-proxy/README.md` and updated `deploy/README.md` to record host routing invariants and repository ownership of production reverse proxy configuration.

## Result

Repository review confirms the current baseline is a single-service app that serves API and client assets, while the existing deploy flow already supports whole-compose rebuilds. The target split-host architecture is now explicitly documented in the repository: `<root-domain>` is reserved for a future `landing` service, `www.<root-domain>` redirects to the canonical root host, `assistant.<root-domain>` remains on `app`, and production reverse proxy configuration is versioned under `deploy/reverse-proxy/`. No runtime smoke or production DNS verification was executed in this step.
