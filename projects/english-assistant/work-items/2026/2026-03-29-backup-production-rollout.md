---
date: 2026-03-29
recorded_at: 2026-03-29T10:41:16.609Z
project: english-assistant
topic: backup-production-rollout
source: agent
status: active
work_item_state: open
---
# Work Item

## Summary

Roll out the backup pipeline on the real VPS: install scheduled execution, connect external storage, and validate restore from a real backup.

## Outcome

The target VPS runs scheduled backups, copies them to the chosen external storage, and a restore procedure is validated against a real backup artifact.

## Provenance

- decision:english-assistant:2026-03-17:backup-strategy

## Dependencies

- work-item:english-assistant:2026-03-17:backup
- work-item:english-assistant:2026-03-29:deploy-webhook-vps-rollout

## Context

- none

## Verification

- Cron or equivalent scheduler is installed on the target VPS and executes deploy/backup.sh with the intended retention policy.
- An external backup provider is configured and receives the produced SQLite backup copy.
- Restore of the application database from a real backup artifact is validated on the target or an equivalent host.
- Provider-specific environment, paths, retention, and recovery steps are documented for production use.

## Evidence

- none
