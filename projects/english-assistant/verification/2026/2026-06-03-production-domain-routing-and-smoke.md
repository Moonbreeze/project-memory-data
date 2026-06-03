---
date: 2026-06-03
recorded_at: 2026-06-03T10:14:13.207Z
project: english-assistant
topic: production-domain-routing-and-smoke
source: agent
status: active
---
# Verification Result

## Scope

repo-side production domain routing contract and local hostname smoke

## Steps

- Ran `pnpm test` and confirmed the repository test suite stayed green after adding reverse proxy routing and landing CTA host-resolution coverage.
- Ran `pnpm smoke:reverse-proxy` and verified the local hostname contract: root-domain -> landing, `www` -> canonical redirect, `assistant` -> app.

## Result

Repository verification passed. The local routing contract is covered and confirmed, while real public-domain verification on the production VPS is intentionally deferred to a separate infra follow-up item.
