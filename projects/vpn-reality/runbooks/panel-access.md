---
date: 2026-10-11
recorded_at: 2026-10-11T20:00:03.293Z
project: vpn-reality
topic: panel-access
source: agent
status: active
---
# Runbook

## Purpose

Безопасный доступ к 3x-ui панели через SSH-туннель без домена и TLS.

## Procedure

- С Windows поднять локальный форвард командой `ssh -L 29486:127.0.0.1:29486 -N dev`; локальный SSH alias `dev` содержит username, identity и порт DE exit 147.45.196.137.
- Оставить терминал работающим: `-N` не открывает remote shell, туннель активен пока жив SSH-процесс.
- Открыть в браузере `http://127.0.0.1:29486/CBBrgsrNZfY43jtrAY/`.
- Войти под single-admin учёткой; пароль хранится только в личном менеджере.
- По окончании остановить туннель через Ctrl+C.

## Verification

- `curl -sS -o /dev/null -w '%{http_code}\n' http://127.0.0.1:29486/CBBrgsrNZfY43jtrAY/` на рабочей машине возвращает 200.
- На DE `sudo ss -ltnp` показывает порт 29486 только на 127.0.0.1, не на внешнем IP.
- На DE `sudo ufw status` не содержит публичного allow для 29486/tcp.
