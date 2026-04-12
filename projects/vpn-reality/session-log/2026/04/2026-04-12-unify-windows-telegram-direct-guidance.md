---
date: 2026-04-12
recorded_at: 2026-04-12T10:38:54.129Z
project: vpn-reality
topic: unify-windows-telegram-direct-guidance
source: agent
status: active
---
# Session Note

## Summary

Обновлены stable docs и verification под модель, где Telegram Desktop не является проверкой TUN и при отдельном MTProto выводится из VPN через process-based direct rule в Karing.

## Actions

- Переписан canonical-doc clients.md: Windows-клиент описан как Karing + TUN + remote .srs rule-set'ы runetfreedom.
- Добавлено guidance, что Telegram Desktop не является verification target для TUN при отдельном MTProto.
- Зафиксирован способ исключения Telegram из VPN в Karing: custom diversion group с действием Direct и правилом Process name = Telegram.exe, при необходимости — точный Process path.
- Переписан runbook add-device.md под Karing + TUN и добавлен шаг по исключению Telegram из VPN.
- Обновлён verification в work-item unify-windows-hiddify-next: вместо Telegram используется non-browser приложение без собственного proxy-стека.

## Follow-up

- Живая валидация на Windows: проверить, что telegram-direct действительно матчится по Process name или Process path.
- После живой валидации создать verification-result и при необходимости уточнить runbook, если имя процесса или путь Telegram отличаются для desktop portable/store сборок.
