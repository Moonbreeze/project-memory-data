---
date: 2026-04-19
recorded_at: 2026-04-19T13:47:00.972Z
project: english-assistant
topic: deploy-webhook-vps-rollout
source: agent
status: active
---
# Session Note

## Summary

Completed the VPS webhook rollout for production: mapped aevumi.ru/assistant.aevumi.ru to the host, configured nginx and TLS, deployed the Docker app plus systemd-managed webhook listener, aligned the deploy flow to master, and verified post-reboot auto-recovery. During rollout we also fixed webhook acknowledgement timing, deploy compose override handling, and container restart policy.

## Actions

- Configured DNS, nginx reverse proxy, and HTTPS for aevumi.ru, www.aevumi.ru, and assistant.aevumi.ru with the app served on assistant.aevumi.ru and the webhook endpoint on /github.
- Provisioned the VPS runtime for this repo: Docker app on localhost port 3001 behind nginx, webhook listener as a systemd service, GitHub webhook secret/env, and branch alignment from main to master for both DEPLOY_TARGET_REF and DEPLOY_GIT_BRANCH.
- Committed and pushed three production fixes during rollout: immediate webhook acknowledgement before deploy completion, deploy-script support for compose overrides/default project-directory compose invocation, and restart policy for the app container so reboot recovery works.
- Validated the end-to-end path with real GitHub push-triggered deployment and then confirmed reboot recovery by checking that the app container and webhook listener came back automatically after VPS restart.

## Follow-up

- Create a dedicated rollout slice to reduce or eliminate brief 502 responses during docker rebuilds on the single-host VPS deployment path.
- Proceed with backup-production-rollout now that the webhook VPS rollout dependency is completed.
