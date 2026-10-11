---
date: 2026-10-11
recorded_at: 2026-10-11T08:51:32.168Z
project: vpn-reality
topic: reproducible-ru-relay-project
source: agent
status: active
work_item_state: done
---
# Work Item

## Summary

Создан локальный проект /home/moonbreeze/vpn-relay-bootstrap для воспроизводимого Xray/HAProxy/WireGuard RU entry на чистой Ubuntu24.04 без образа с секретами.

## Outcome

Code-проект создан, git инициализирован без коммитов; private render/dry-run/apply/check tooling и README готовы. Offline tests и parser checks пройдены, live deploy и end-to-end verification явно оставлены отдельному VDSina trial.

## Provenance

- ad-hoc: Пользователь согласовал configuration-as-code вместо snapshot и после запроса обязательного плана утвердил конкретные файлы, local tests и три project-memory документа ответом +. SSH-ключ генерирует пользователь; инфраструктуру в этом work slice не менять.

## Dependencies

- none

## Context

- none

## Verification

- Ни одного живого ключа, UUID или MTProto secret в Git/памяти.
- Конфигурации сохраняют relay-first VPN и отдельный WireGuard MTProto транспорт с send-proxy-v2.
- По умолчанию генерация/проверки не запускают установку и не меняют firewall/сервисы.
- Автоматические тесты проверяют валидацию ввода, маршрутизацию, права на секретные артефакты и повторяемость.
- README описывает DE allowlist, независимый WG peer, клиентские ссылки и безопасный rollback.

## Evidence

- session-note:vpn-reality:2026-10-11:relay-bootstrap-initial-project
- verification-result:vpn-reality:2026-10-11:relay-bootstrap-initial-project
