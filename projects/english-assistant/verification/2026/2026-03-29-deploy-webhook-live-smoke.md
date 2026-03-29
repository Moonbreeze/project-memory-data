---
date: 2026-03-29
recorded_at: 2026-03-29T09:57:48.991Z
project: english-assistant
topic: deploy-webhook-live-smoke
source: agent
status: active
---
# Verification Result

## Scope

deploy webhook live smoke

## Steps

- Запущен единый live smoke runner `pnpm smoke:deploy-webhook-live` вне sandbox для возможности bind на localhost
- Поднят standalone webhook listener на случайном localhost-порту с `localDeployStub.sh` вместо боевого deploy script
- Проверен сценарий `accepted-main-push`: HTTP 202 Accepted и запись ожидаемых переменных окружения в stub log
- Проверены сценарии `invalid-signature`, `ignored-wrong-ref` и `ignored-unsupported-event`: ответы соответствуют ожиданиям и stub script не вызывается

## Result

`pnpm smoke:deploy-webhook-live` прошёл успешно. Локальный listener принял валидный signed push webhook, вызвал stub deploy script только для `refs/heads/main`, а сценарии `invalid-signature`, `ignored-wrong-ref` и `ignored-unsupported-event` не триггерили deploy flow.
