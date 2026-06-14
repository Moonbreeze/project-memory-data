---
date: 2026-06-14
recorded_at: 2026-06-14T15:12:39.393Z
project: english-assistant
topic: production-reverse-proxy-rollout-and-domain-smoke
source: agent
status: active
---
# Verification Result

## Scope

live VPS hostname routing for the landing/app production split

## Steps

- Verified the effective docker compose topology after removing the stale override and confirmed that both app and landing containers were up on their intended ports.
- Confirmed with curl that https://www.aevumi.ru/ returns a 301 redirect to https://aevumi.ru/.
- Confirmed with curl that https://aevumi.ru/ returns 200 and serves the landing host.
- Confirmed with curl that https://assistant.aevumi.ru/health returns 200 from the application host.
- Confirmed in a clean browser session that the root host opens the landing correctly and that the previous redirect-to-assistant symptom was caused by browser cache.

## Result

Production smoke passed on the live VPS. The public routing now matches the intended contract: root host -> landing, www -> canonical root redirect, assistant subdomain -> app.
