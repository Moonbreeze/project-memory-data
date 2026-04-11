---
date: 2026-04-11
recorded_at: 2026-04-11T17:10:22.968Z
project: vpn-reality
topic: unify-windows-hiddify-next
source: agent
status: active
work_item_state: open
---
# Work Item

## Summary

Проверить наличие ru-blocked(-community).srs у runetfreedom и перевести собственную Windows-машину с v2rayN+xray на Hiddify-Next+sing-box так же, как планируется ставить друзьям «из коробки»: одна subscription-ссылка из 3x-ui, remote rule-set .srs, TUN mode. Суперсидит windows-tun-sing-box-ru-blocked.

## Outcome

Единый Windows-клиент для меня и друзей: Hiddify-Next с subscription из 3x-ui, ru-blocked.srs как remote rule-set, TUN on. v2rayN удалён или оставлен только как fallback. Инструкция для неподкованного друга укладывается в ≤4 шага.

## Provenance

- ad-hoc: Унификация клиентского стека: чтобы поддержка друзей не требовала второй ветки настроек и чтобы централизованное обновление правил на панели доезжало одинаково до всех устройств. Пересекается с windows-tun-sing-box-ru-blocked — тот закрыт как superseded.

## Dependencies

- none

## Context

- none

## Verification

- ru-blocked.srs и ru-blocked-community.srs найдены в публичном репо runetfreedom, либо успешно скомпилированы локально через sing-box rule-set compile.
- Hiddify-Next на Windows импортирует subscription из 3x-ui без ошибок; профиль содержит remote rule-set на .srs.
- TUN mode включён; ya.ru идёт direct и показывает российский IP; заблокированный в РФ домен открывается через DE-exit.
- v2rayN остановлен/удалён; non-HTTP приложения (Telegram Desktop) корректно ходят через тоннель.
- Инструкция для друга укладывается в ≤4 шага со скриншотами.

## Evidence

- none
