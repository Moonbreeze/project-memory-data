---
date: 2026-10-08
recorded_at: 2026-10-08T06:09:52.822Z
project: vpn-reality
topic: relay-outage-direct-de-fallback
source: agent
status: active
---
# Session Note

## Summary

При одновременном отказе VPN и Telegram локализована недоступность общего Yandex relay. Пользователь настроил временный прямой VLESS Reality на DE по предложенным шагам и подтвердил успешное подключение.

## Actions

- Прочитаны topology, security-model, client-setup и runbooks для relay и MTProto.
- На DE подтверждены работающие x-ui/Xray, mtg и wg-mtg; IPv4/IPv6 egress и www.cloudflare.com доступны.
- С DE TCP 178.154.193.39:22/443/9443 завершается таймаутом; публичный relay и 10.66.0.1 не отвечают на ping. Пользователь сообщил о проблемах у Yandex Cloud; независимое подтверждение статуса провайдера не получено, status page требует JavaScript.
- sudo в агентской сессии требует пароль; административные действия выполнял пользователь в своём SSH-терминале, пароль в чат не передавался.
- Пользователю предоставлены шаги создания отдельного temporary-direct-de inbound DE:443 с VLESS Reality Vision и www.cloudflare.com, новой keypair/short-id/client UUID и отдельным IPv4 UFW allow; существующий relay-backhaul и приватный mtg backend не должны изменяться.
- Пользователь сообщил: всё подключилось успешно. Отдельные результаты mobile-network, IP echo и Telegram checks не представлены.
- Архитектура relay-first остаётся целевой; direct-DE профиль является временным исключением на время инцидента, без сохранения private keys, UUID или share-ссылок в памяти.

## Follow-up

- После восстановления Yandex проверить публичные 443/9443, WireGuard handshake и HAProxy backend; выполнить live VPN и Telegram проверки.
- Вернуть устройства на relay-first профили. Через 3x-ui удалить/отключить только temporary-direct-de inbound; в sudo ufw status numbered найти и удалить только правило с комментарием temporary direct Reality, не трогая 8443/3128/SSH.
- Подтвердить закрытие direct DE:443 и сохранение приватного mtg backend.
