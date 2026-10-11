---
date: 2026-10-11
recorded_at: 2026-10-11T21:24:08.767Z
project: vpn-reality
topic: client-link-retrieval
source: agent
status: active
---
# Runbook

## Purpose

Безопасно доставить committed vpn-relay-bootstrap и получить актуальные VLESS/MTProto ссылки с Windows, не копируя DE MTProto secret в relay config.

## Procedure

- В Windows checkout `vpn-relay-bootstrap` выполнить `git pull --ff-only`.
- После изменений проекта доставить committed HEAD командой `.\deliver.ps1 ruhop`; script использует SSH alias и не запускает bootstrap.
- Убедиться, что на relay применена shared VLESS label `ruhop-shared`; общий UUID хранится только в protected config.
- Из корня checkout выполнить `.\get-links.ps1`. Ввести sudo password для `dev`, когда OpenSSH откроет интерактивный prompt.
- Скрипт генерирует VLESS на `ruhop`, временно копирует committed `client_links.py` на `dev`, читает `/etc/mtg.toml` с допустимыми permissions 0600 root-only или 0640 root:mtg и формирует Telegram endpoint 138.16.175.166:9443.
- Скопировать нужные links из terminal output в клиенты. Не помещать output в chat, документацию, tickets или логи.
- Temporary DE/local files удаляются автоматически. При ошибке не обходить permission/committed-helper checks; исправить причину и повторить.

## Verification

- `deliver.ps1` сообщает delivered commit и `Bootstrap was not run`.
- `get-links.ps1` выводит секции `VLESS (ruhop-shared via ruhop)` и `Telegram MTProto (via 138.16.175.166:9443)`.
- Импортированный VLESS получает DE egress, Telegram proxy подключается и передаёт сообщения/media.
- На DE mtg config остаётся 0640 root:mtg или строже; secret не появляется на ruhop или в project-memory.
