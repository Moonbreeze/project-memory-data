---
date: 2026-04-19
recorded_at: 2026-04-19T13:47:17.363Z
project: english-assistant
topic: deploy-zero-downtime-rollout
source: agent
status: active
work_item_state: open
---
# Work Item

## Summary

Убрать или контролируемо заменить краткий 502-downtime во время production deploy на VPS.

## Outcome

Production deploy выполняется без raw 502 для пользователей либо с явной controlled strategy (например maintenance page, staged swap или иной согласованный rollout-mechanism).

## Provenance

- ad-hoc: Follow-up slice opened after the production VPS webhook rollout exposed brief 502 responses during docker rebuild/recreate on deploy.

## Dependencies

- work-item:english-assistant:2026-03-29:deploy-webhook-vps-rollout

## Context

- none

## Verification

- Во время production deploy пользовательский трафик больше не получает неожиданный raw 502 от nginx/app handoff.
- Выбранная стратегия rollout documented and reproducible for future deploys on the VPS.
- End-to-end deploy по GitHub webhook подтверждает ожидаемое поведение без regressions для app и webhook availability.

## Evidence

- none
