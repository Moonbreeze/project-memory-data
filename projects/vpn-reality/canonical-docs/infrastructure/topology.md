---
date: 2026-04-11
recorded_at: 2026-04-11T16:09:01.612Z
project: vpn-reality
topic: topology
registry_scope: infrastructure
source: agent
status: active
---
# Canonical Doc

## Summary

Топология текущей инсталляции VPN: один зарубежный VPS с 3x-ui/Xray, VLESS Reality + Vision flow на :443, два клиента. Share-ссылки генерируются с публичным IP благодаря External Proxy override на inbound.

## Guidance

- Зарубежный VPS: `vm1184299.cloud.nuxt.network`, внешний IPv4 `147.45.196.137`, IPv6 `2a0f:cdc6:500:758::2`. Дата-центр заявлен в Германии. Хостер — Aeza (или дочерний бренд). BBR + fq уже в дефолте ядра Ubuntu 22.04.
- OS: Ubuntu 22.04.5 LTS. Пользователь `moonbreeze` в группах sudo+docker. SSH на нестандартном порту `51218`, только pubkey (password auth disabled). В `~/.ssh/authorized_keys` два ключа: `moonbreeze@HUMGATE` (основной рабочий ноут) и `moonbreeze@moonbreeze-o`.
- ufw rules: allow 51218/tcp (SSH), 443/tcp 8443/tcp 2053/tcp (VLESS Reality слоты). Порты 8443 и 2053 зарезервированы, но сейчас не используются — только 443 активен. 80/tcp закрыт намеренно (нет домена → нет Let's Encrypt).
- 3x-ui панель: порт `29486`, WebBasePath `/CBBrgsrNZfY43jtrAY/`, слушает на всех интерфейсах. Порт 29486 в ufw закрыт — доступ только через SSH-туннель. Subscription server 3x-ui на порту `2096` (не используется, см. decision profile-file-over-subscription-url). Xray core: 26.2.6. 3x-ui: 2.8.11.
- Inbound `reality-main` на порту 443: VLESS + Reality + TCP + xtls-rprx-vision flow. SNI-маска: `www.microsoft.com` (fallback `microsoft.com:443`). Fingerprint: `chrome`. Reality public key: `9hE2DLpR6caqCS8FRZ9N4n2fsPTXcDuhVsuvXoGyAw8`. Short IDs пул из 8 штук, в share-ссылках используется `444a941e4b8f`. SpiderX: `/`.
- В inbound `reality-main` настроен External Proxy entry с `Forced Expose IP = 147.45.196.137`, `Port = 443`, `Remark = public-ipv4`. Это заставляет 3x-ui подставлять публичный IP в генерируемые `vless://` ссылки независимо от того, через какой URL открыта панель (включая 127.0.0.1 через SSH-туннель). Ручная замена хоста в экспортируемых ссылках больше не требуется. Side-effect: к remark клиента в ssh-fragment'е ссылки подклеивается суффикс `-public-ipv4` (косметика).
- Клиенты в inbound: `phone-android` (UUID `4f26c1dc-2b1d-456f-95d7-57dea285c246`) и `desktop-windows` (UUID `1d27dd21-0bda-417b-a43f-c77aca64ca3a`). Оба с flow `xtls-rprx-vision`. Каждое устройство имеет свой UUID для независимой статистики и отзыва.
- Xray routing rules активные: `geoip:private → blocked`, `geoip:ru → blocked`, `protocol:bittorrent → blocked`. Правило `geoip:ru → blocked` — митигация уязвимости клиентского SOCKS5 (см. decision security/geoip-ru-blackhole). Outbounds: `direct` (freedom) и `blocked` (blackhole).

## References

- runbook:vpn-reality:operations:panel-access
- runbook:vpn-reality:clients:add-client
- decision:vpn-reality:security:geoip-ru-blackhole
- decision:vpn-reality:operations:ssh-tunnel-over-le
- decision:vpn-reality:2026-04-11:profile-file-over-subscription-url
- verification-result:vpn-reality:2026-04-11:panel-external-proxy-public-ip
- https://habr.com/ru/articles/1021160/
