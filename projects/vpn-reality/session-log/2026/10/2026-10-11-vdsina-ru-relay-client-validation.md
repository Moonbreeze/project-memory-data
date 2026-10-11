---
date: 2026-10-11
recorded_at: 2026-10-11T20:39:42.320Z
project: vpn-reality
topic: vdsina-ru-relay-client-validation
source: agent
status: active
---
# Session Note

## Summary

Пользователь завершил внешнюю клиентскую проверку нового VDSina relay для VLESS Reality и Telegram MTProto; оба пути работают через существующий DE exit.

## Actions

- Создан отдельный VLESS клиентский профиль для нового relay 138.16.175.166:443 с новым client UUID и relay Reality keypair.
- Пользователь импортировал профиль и подтвердил ожидаемый DE egress, доступность сайтов и reconnect.
- Создана MTProto ссылка с новым endpoint 138.16.175.166:9443 и существующим защищённым DE mtg secret без публикации secret в чат или project-memory.
- Пользователь подтвердил Telegram Connected, передачу сообщений, media и reconnect через новый relay.
- Temporary direct-DE Reality, старый Yandex WireGuard peer и старые DE firewall rules намеренно не удалялись без отдельного подтверждения.

## Follow-up

- После выбранного пользователем периода наблюдения удалить temporary direct-DE inbound/rule, если резерв больше не нужен.
- Отдельно решить судьбу старого Yandex peer и его адресных DE firewall rules; не удалять их вместе с temporary direct-DE без явного решения.
- Сохранить новые клиентские ссылки и ключевой материал в защищённом хранилище.
