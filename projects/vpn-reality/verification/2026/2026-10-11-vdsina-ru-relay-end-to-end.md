---
date: 2026-10-11
recorded_at: 2026-10-11T20:39:42.339Z
project: vpn-reality
topic: vdsina-ru-relay-end-to-end
source: user
status: active
---
# Verification Result

## Scope

Полная внешняя проверка VLESS Reality и Telegram MTProto через новый VDSina RU relay 138.16.175.166 к DE exit.

## Steps

- Пользователь импортировал новый VLESS Reality профиль endpoint 138.16.175.166:443.
- Пользователь подтвердил успешную проверку DE egress, рабочих сайтов и reconnect через новый VPN профиль.
- Проверена публичная TCP-доступность нового Telegram frontend 138.16.175.166:9443.
- Пользователь добавил новый Telegram proxy endpoint с существующим mtg secret.
- Пользователь подтвердил Telegram Connected, отправку/получение сообщений, загрузку media и reconnect.
- Ранее server-side check подтвердил свежий WireGuard handshake, DE:8443, private mtg backend 10.66.0.2:3128 и HAProxy backend UP.

## Result

Проверка пройдена. Новый VDSina relay полностью работоспособен для VPN и Telegram через существующий DE exit. Temporary direct-DE и старые Yandex access rules остаются только как неубранный резерв до отдельного решения.
