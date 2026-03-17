---
date: 2026-03-17
project: english-assistant
topic: deploy-via-git
source: user
status: active
---
# Decision

## Context

Нужен удобный деплой без ручного ssh + pull + rebuild каждый раз. Код будет на GitHub. Один разработчик.

## Decision

Деплой через GitHub webhook. В репо директория deploy/ с webhook-listener (Node.js или bash) и deploy-скриптом. Listener запускается на хосте через systemd, слушает webhook от GitHub, валидирует GitHub secret. При получении push-события запускает deploy.sh: бэкап БД, git pull, docker compose up -d --build. Listener работает на хосте, не в Docker-контейнере.

## Consequences

- deploy/ в репо: webhook-listener, deploy.sh, systemd unit-файл
- На VPS нужен Node.js или bash на хосте (не только в Docker)
- Нужен GitHub webhook secret в .env на хосте
- Открытый порт для webhook-listener на VPS
- Бэкап БД встроен в deploy-скрипт — согласуется с backup-strategy
