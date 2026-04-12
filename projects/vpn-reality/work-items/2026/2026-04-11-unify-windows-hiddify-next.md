---
date: 2026-04-11
recorded_at: 2026-04-11T17:10:22.968Z
project: vpn-reality
topic: unify-windows-hiddify-next
source: agent
status: active
work_item_state: in_progress
---
# Work Item

## Summary

Проверить наличие готовых sing-box .srs rule-set'ов у runetfreedom (ru-blocked, ru-blocked-community) или скомпилировать их локально через sing-box rule-set compile. Перевести собственную Windows-машину с v2rayN+xray+System Proxy на Hiddify-Next+sing-box+TUN так же, как планируется ставить друзьям. Клиентский профиль раздаётся файлом/clipboard один раз через защищённый канал (см. decision profile-file-over-subscription-url) — subscription-URL не используется. Суперсидит windows-tun-sing-box-ru-blocked.

## Outcome

Единый Windows-клиент для меня и друзей: Hiddify-Next с профилем, импортированным из файла/clipboard, ru-blocked(-community) rule-set (remote с raw URL из runetfreedom если доступно, иначе локально скомпилированный .srs захостенный либо как GitHub Gist raw, либо в нашем self-hosted месте), TUN mode включён. v2rayN остановлен или оставлен только как fallback. Инструкция для неподкованного друга укладывается в ≤4 шага. Canonical-doc client-setup/clients.md и runbook add-device.md обновлены под новый клиентский стек и файловую доставку профиля.

## Provenance

- ad-hoc: Унификация клиентского стека: чтобы поддержка друзей не требовала второй ветки настроек и чтобы централизованное обновление правил runetfreedom доезжало одинаково до всех устройств. Пересекается с windows-tun-sing-box-ru-blocked — тот закрыт как superseded. Связан с decision profile-file-over-subscription-url, который явно исключает subscription-URL как способ доставки профиля.

## Dependencies

- none

## Context

- decision:vpn-reality:2026-04-11:profile-file-over-subscription-url
- decision:vpn-reality:2026-04-11:windows-system-proxy-over-tun
- canonical-doc:vpn-reality:client-setup:clients

## Verification

- Research-гейт: проверена репа runetfreedom на наличие готовых .srs rule-set'ов; зафиксирован вывод в session-note.
- Если .srs доступны официально — используется remote URL; если нет — скомпилированы локально через sing-box rule-set compile и захостены (средство хостинга выбирается в ходе исполнения).
- Hiddify-Next на Windows установлен, профиль импортирован из файла/clipboard без ошибок; routing содержит правила ru-blocked → proxy, ru/cn → direct.
- TUN mode включён; ya.ru идёт direct и показывает российский IP; заблокированный в РФ домен открывается через DE-exit.
- v2rayN остановлен/удалён; non-HTTP приложения (Telegram Desktop, другие не-браузерные apk) корректно ходят через тоннель через TUN.
- Инструкция для друга укладывается в ≤4 шага и не требует никакого публичного endpoint кроме самого VLESS inbound на :443.
- Canonical-doc client-setup/clients.md обновлён под Hiddify-Next+TUN и файловую доставку; runbook add-device.md переписан под новый стек на обеих платформах; действующий decision windows-system-proxy-over-tun суперсидирован новым.

## Evidence

- none
