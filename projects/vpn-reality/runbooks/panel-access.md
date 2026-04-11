---
date: 2026-04-11
recorded_at: 2026-04-11T16:23:10.281Z
project: vpn-reality
topic: panel-access
source: agent
status: active
---
# Runbook

## Purpose

Безопасный доступ к 3x-ui панели через SSH-туннель без домена и TLS.

## Procedure

- С рабочей машины поднять локальный форвард: `ssh -L 29486:127.0.0.1:29486 -N aeza-de` (алиас в ~/.ssh/config указывает на moonbreeze@147.45.196.137).
- Оставить терминал висеть — `-N` не выдаёт remote shell, туннель активен пока процесс жив.
- Открыть в браузере `http://127.0.0.1:29486/CBBrgsrNZfY43jtrAY/`.
- Залогиниться учёткой админа (single-admin режим, пароль хранится в личном менеджере).
- По завершении работы — Ctrl+C в терминале с туннелем.

## Verification

- `curl -sS -o /dev/null -w '%{http_code}\n' http://127.0.0.1:29486/CBBrgsrNZfY43jtrAY/` возвращает 200.
- На VPS `sudo ss -ltnp | grep 29486` показывает listen только на 127.0.0.1, не на внешнем IP.
- `sudo ufw status` не содержит правила для 29486/tcp.
