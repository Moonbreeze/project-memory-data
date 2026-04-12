---
date: 2026-04-12
recorded_at: 2026-04-12T09:55:25.291Z
project: vpn-reality
topic: unify-windows-hiddify-next
source: agent
status: active
work_item_state: in_progress
---
# Work Item

## Summary

Перевести Windows-клиент с v2rayN+Xray+System Proxy на TUN mode с sing-box и remote .srs rule-set'ами от runetfreedom. Первичный кандидат — Karing (sing-box core, простой UI, кроссплатформа). Fallback — v2rayN+TUN с Russia preset. Hiddify-Next отпал: не поддерживает кастомный routing / remote rule-set'ы (подтверждено: issue #904 closed as not planned, официальная документация от января 2026). Профиль раздаётся файлом/clipboard (decision profile-file-over-subscription-url). Research-гейт пройден: runetfreedom публикует .srs на ветке release (geosite-ru-blocked.srs, geoip-ru-blocked.srs, geoip-ru-blocked-community.srs — все HTTP 200, обновляются каждые 6 часов).

## Outcome

Единый Windows-клиент для себя и друзей с TUN mode, split routing (ru-blocked → proxy, ru/private → direct) через remote .srs rule-set'ы runetfreedom. v2rayN остановлен или удалён. Инструкция для друга ≤4 шага. Canonical-doc clients.md и runbook add-device.md обновлены. Decision windows-system-proxy-over-tun суперсидирован новым.

## Provenance

- ad-hoc: Унификация клиентского стека. Пересмотр после обнаружения, что Hiddify-Next не поддерживает кастомный routing. Runetfreedom .srs rule-set'ы теперь доступны — снимают оригинальный блокер TUN mode (sing-box не мог читать geosite.dat).

## Dependencies

- none

## Context

- decision:vpn-reality:2026-04-11:profile-file-over-subscription-url
- decision:vpn-reality:2026-04-11:windows-system-proxy-over-tun
- canonical-doc:vpn-reality:client-setup:clients

## Verification

- Research-гейт (DONE): runetfreedom публикует .srs — geosite-ru-blocked.srs, geoip-ru-blocked.srs, geoip-ru-blocked-community.srs на raw.githubusercontent.com/.../release/sing-box/rule-set-{geosite,geoip}/. Все HTTP 200.
- Hiddify-Next отклонён (DONE): кастомный routing не поддерживается (issue #904 not planned, офиц. документация от января 2026 подтверждает).
- Выбор клиента: Karing (primary) или v2rayN+TUN (fallback). Валидация Karing: TUN на Windows работает, импорт одиночной vless:// ссылки проходит, remote .srs rule-set подключается.
- Клиент установлен на Windows, профиль импортирован из файла/clipboard; routing: ru-blocked → proxy, ru/private → direct.
- TUN mode включён; ya.ru → direct, российский IP; заблокированный домен → через DE-exit.
- Хотя бы одно non-browser приложение без собственного proxy-стека корректно ходит через TUN.
- Если Telegram Desktop использует отдельный MTProto, он исключён из VPN через process-based direct rule и не используется как индикатор корректности TUN.
- Инструкция для друга ≤4 шага, не требует публичных endpoint'ов кроме VLESS :443.
- Canonical-doc clients.md обновлён под новый клиент+TUN и файловую доставку профиля.
- Runbook add-device.md переписан под новый клиентский стек.
- Decision windows-system-proxy-over-tun суперсидирован новым decision.

## Evidence

- session-note:vpn-reality:2026-04-12:unify-windows-research
- session-note:vpn-reality:2026-04-12:unify-windows-karing-prep
- session-note:vpn-reality:2026-04-12:unify-windows-telegram-direct-guidance
