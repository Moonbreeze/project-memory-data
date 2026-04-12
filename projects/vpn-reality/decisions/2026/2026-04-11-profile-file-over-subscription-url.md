---
date: 2026-04-11
recorded_at: 2026-04-11T17:28:27.115Z
project: vpn-reality
topic: profile-file-over-subscription-url
source: agent
status: active
---
# Decision

## Context

Work-item unify-windows-hiddify-next изначально требовал централизованной subscription-URL из 3x-ui для Hiddify-Next на Windows и Android. Это вытянуло за собой work-item panel-domain-and-le-cert: публичный HTTPS endpoint на subscription-server 3x-ui (:2096) требует TLS, TLS требует домен, домен требует регистрацию/оплату/WHOIS-гигиену/CT-логи. Обсуждение показало, что существующий decision ssh-tunnel-over-le остаётся валидным для админ-доступа к web UI панели (SSH local port forward, :29486 закрыт в ufw). Реальный драйвер публичного endpoint — не админ-доступ, а возможность обновлять клиентский профиль удалённо (друзья не могут поднять SSH). Для текущего user-base (2 своих устройства + до 2 друзей, редкая ротация inbound-параметров) централизованное обновление не окупает стоимость покупки домена, открытия :80/:8443 в ufw, расширения поверхности атаки и засветки домена в публичных Certificate Transparency логах.

## Decision

Клиентский профиль для Hiddify-Next (и любого другого VLESS-клиента) раздаётся файлом или vless://-ссылкой один раз через защищённый канал при первой настройке устройства. Публичный subscription-URL не используется. Subscription-server 3x-ui на порту 2096 остаётся закрытым в ufw. Домен для проекта не регистрируется. Существующий decision ssh-tunnel-over-le остаётся в силе без изменений. Work-item panel-domain-and-le-cert переводится в canceled (формулировка устарела) и при появлении реальной потребности будет пересоздан с новым скоупом (TLS только для subscription-server, панель UI остаётся на SSH-туннеле). Триггеры для пересоздания: user-base ≥5 активных устройств ИЛИ частая ротация UUID/short-ID/SNI (чаще ~раз в квартал), при которой ручная передача профиля становится операционно болезненной.

## Consequences

- Плюс: домен покупать не надо — $0, ноль времени, ноль WHOIS-гигиены, ноль засветки в CT-логах.
- Плюс: поверхность атаки VPS не растёт — порты 80 и 8443 остаются закрыты в ufw, LE не настраивается, cron/renew не поддерживается.
- Плюс: существующий ssh-tunnel-over-le продолжает работать без изменений — админ-доступ к панели 3x-ui остаётся через SSH local port forward, как сейчас.
- Плюс: security-model не теряет уровней — CVE-митигации (geoip:ru blackhole, Reality SNI маскировка, pubkey-only SSH) работают так же.
- Минус: при любом изменении inbound-параметров (UUID, short ID, SNI-маска, публичный IP VPS) надо перевыдавать профиль каждому устройству вручную через защищённый канал. Для 2–4 устройств приемлемо, для больше — нет.
- Минус: ротация ключей Reality (pbk/private key) становится операционно дорогой — все клиенты разом перестанут подключаться, пока им не раздадут новый файл. Это надо учесть при планировании ротации.
- Минус: если user-base вырастет или появится регулярная ротация, придётся расчехлять panel-domain-and-le-cert с нуля — домен, LE, ufw-правки, новый decision отменяющий этот.

## Stable Guidance Review

- Outcome: update-required
- Summary: Reviewed current stable guidance and identified a follow-up update requirement.
- Note: Canonical-doc client-setup/clients.md и runbook add-device.md требуют обновления под файловую доставку профиля (Hiddify-Next import from clipboard/file, без subscription-URL). Обновление выполняется в рамках исполнения work-item unify-windows-hiddify-next в том же слайсе, где меняется Windows-клиент на Hiddify-Next+TUN. Не выносится отдельно, чтобы избежать документного drift между canonical-doc и реально работающей инсталляцией.
