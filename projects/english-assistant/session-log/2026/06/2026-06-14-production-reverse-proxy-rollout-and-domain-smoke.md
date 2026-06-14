---
date: 2026-06-14
recorded_at: 2026-06-14T15:12:39.364Z
project: english-assistant
topic: production-reverse-proxy-rollout-and-domain-smoke
source: agent
status: active
---
# Session Note

## Summary

On the live VPS, removed the stale compose override, restored the correct app/landing topology, switched the public hostname routing through the existing nginx proxy, and validated the root, www, and assistant hosts against the intended production contract.

## Actions

- Removed the stale compose override that published 127.0.0.1:3001->3000 for the app service and prevented the landing service from binding its public port.
- Recreated the app and landing containers so the production topology matched the repository contract: app on 3000 and landing on 3001.
- Updated the live nginx configuration so aevumi.ru proxies to landing, www.aevumi.ru redirects to the canonical root host, and assistant.aevumi.ru proxies to the app service while preserving the /github webhook route.
- Verified that the remaining redirect-to-assistant symptom in the original browser was caused by a cached 301 rather than a live server-side routing issue.

## Follow-up

- Keep Caddy disabled because the production reverse proxy is handled by nginx on this VPS.
- Continue checking live hostname routing after future deploys that touch container ports or public host configuration.
