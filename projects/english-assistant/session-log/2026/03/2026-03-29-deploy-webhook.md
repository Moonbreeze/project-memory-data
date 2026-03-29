---
date: 2026-03-29
recorded_at: 2026-03-29T09:57:49.081Z
project: english-assistant
topic: deploy-webhook
source: agent
status: active
---
# Session Note

## Summary

Реализован standalone deploy webhook flow с локально проверяемым deploy script, тестами и единым live smoke runner; production activation на реальном VPS вынесен в отдельный follow-up.

## Actions

- Добавлен каталог `deploy/` со standalone webhook listener, HMAC-валидацией GitHub webhook, сериализованным запуском deploy script и шаблоном systemd unit
- Реализован `deploy.sh` с последовательностью backup -> git pull -> docker compose up и `localDeployStub.sh` для безопасных локальных smoke-проверок
- Добавлены unit/integration тесты для webhook handler, HTTP request routing и deploy shell flow; `pnpm test` проходит
- Добавлен единый live smoke runner `pnpm smoke:deploy-webhook-live`, который поднимает listener, прогоняет accepted/invalid-signature/wrong-ref/unsupported-event сценарии и проверяет stub log

## Follow-up

- Установить webhook listener на реальный VPS, подготовить environment file и systemd unit deployment
- Настроить GitHub webhook на целевой хост и проверить доставку реального push event
- Подтвердить systemd autostart и поведение после reboot на VPS
