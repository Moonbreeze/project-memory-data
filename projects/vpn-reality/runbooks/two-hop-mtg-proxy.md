---
date: 2026-08-14
recorded_at: 2026-08-14T07:10:45.200Z
project: vpn-reality
topic: two-hop-mtg-proxy
source: agent
status: active
---
# Runbook

## Purpose

Развернуть, проверить или восстановить постоянный MTProto proxy по пути Yandex relay:9443 -> HAProxy -> WireGuard -> DE mtg, не затрагивая Xray Reality на 443/tcp.

## Procedure

- До изменений проверить, что relay:9443/tcp свободен, Xray продолжает слушать 443/tcp, а на DE свободен приватный backend 10.66.0.2:3128.
- Создать отдельную WireGuard keypair на каждом узле. Private keys хранить только в /etc/wireguard с mode 0600; в project-memory их не записывать.
- На DE создать wg-mtg с Address 10.66.0.2/30, ListenPort 51820 и peer relay с AllowedIPs 10.66.0.1/32. На relay создать wg-mtg с Address 10.66.0.1/30, peer DE, AllowedIPs 10.66.0.2/32, Endpoint 147.45.196.137:51820 и PersistentKeepalive 25.
- На DE разрешить 51820/udp только от публичного IP relay 178.154.193.39. Разрешить 3128/tcp на интерфейсе wg-mtg только от 10.66.0.1 к 10.66.0.2; публичный allow 3128 не создавать.
- На DE установить закреплённую проверенной checksum версию mtg v2. Текущая подтверждённая версия — 2.2.8.
- Сгенерировать FakeTLS secret командой mtg generate-secret --hex cloud.yandex.ru. Secret хранить только в защищённом /etc/mtg.toml и передавать пользователям защищённым каналом; в документацию не включать.
- Настроить mtg с bind-to = 10.66.0.2:3128, proxy-protocol-listener = true и prefer-ip = prefer-ipv6. Запускать отдельным systemd service после wg-quick@wg-mtg.
- На relay добавить HAProxy frontend telegram_mtg_in с bind 0.0.0.0:9443, mode tcp и часовым client timeout. Backend telegram_mtg_out направить на 10.66.0.2:3128 с check, send-proxy-v2 и часовым server timeout.
- Провалидировать /etc/haproxy/haproxy.cfg командой haproxy -c до reload. Открыть 9443/tcp во внешнем Yandex firewall/security group, если такой фильтр включён; локальный UFW на текущем relay неактивен.
- Собрать tg://proxy ссылку с server=178.154.193.39, port=9443 и secret.hex из защищённого DE-конфига. Не использовать автоматически определённые DE IP/3128 из mtg access.
- При недоступности проверять в порядке: публичный bind relay:9443, HAProxy backend state, WireGuard latest handshake/transfer, DE UFW allow на wg-mtg:3128, mtg service/logs, затем client secret/FakeTLS handshake.

## Verification

- На обоих узлах wg show показывает свежий handshake и растущие RX/TX counters; relay пингует 10.66.0.2, DE пингует 10.66.0.1.
- На DE mtg active/enabled и ss показывает только 10.66.0.2:3128, без 0.0.0.0:3128 или публичного DE listener.
- На relay haproxy -c успешен, ss показывает 0.0.0.0:9443, а journal HAProxy показывает backend de_mtg UP.
- С внешней машины устанавливается TCP connection к 178.154.193.39:9443.
- Telegram импортирует tg://proxy ссылку, показывает Connected и передаёт сообщения; для полной проверки дополнительно проверить медиа и reconnect после рестарта.
