---
date: 2026-04-12
recorded_at: 2026-04-12T09:57:07.550Z
project: vpn-reality
topic: unify-windows-research
source: agent
status: active
---
# Session Note

## Summary

Research-фаза work-item unify-windows-hiddify-next: проверка .srs rule-set'ов runetfreedom, оценка Hiddify-Next, сравнительный анализ альтернативных клиентов.

## Actions

- Research-гейт пройден: runetfreedom публикует .srs для sing-box на ветке release. Проверены URL'ы (curl -sI → HTTP 200): geosite-ru-blocked.srs, geosite-ru-blocked-all.srs, geoip-ru-blocked.srs, geoip-ru-blocked-community.srs. Шаблон URL: https://raw.githubusercontent.com/runetfreedom/russia-v2ray-rules-dat/release/sing-box/rule-set-{geosite,geoip}/{type}-{name}.srs. Источник: issue #39 в russia-v2ray-rules-dat.
- Hiddify-Next отклонён: кастомный routing не поддерживается. Подтверждение: GitHub issue #904 closed as 'not planned'; #877 closed as duplicate; официальная документация hiddifynext.app/en/guides/routing-rules/ (январь 2026) явно указывает на отсутствие поддержки и рекомендует альтернативы. Философия проекта — простота, advanced routing 'may not be added in the short term'.
- Сравнительный анализ 5 клиентов: (1) Clash Verge Rev — 110K stars, мощный routing+TUN, но формат правил .mrs несовместим с runetfreedom .srs; (2) Karing — 10.9K stars, sing-box core, .srs native, простой UI, русский QuickStart, кроссплатформа, нужна валидация TUN на Windows; (3) GUI.for.SingBox — 7.5K stars, полный контроль над sing-box, .srs native, но сложнее для друзей; (4) NekoBox — заархивирован (декабрь 2024), не рекомендуется; (5) VeilBox — 18 stars, незрелый, xray core.
- v2rayN как fallback подтверждён: Russia regional preset + remote .srs rule-set'ы + TUN mode через sing-box. Оригинальный блокер (sing-box не мог читать geosite.dat) снят наличием .srs.
- Решение: primary — Karing, fallback — v2rayN+TUN. Work item обновлён.

## Follow-up

- Валидация Karing на Windows: установить, проверить TUN mode, импорт одиночной vless:// ссылки, подключение remote .srs rule-set'ов runetfreedom.
- Если Karing не взлетит — тестировать v2rayN+TUN с Russia preset.
- После выбора клиента: обновить canonical-doc clients.md, runbook add-device.md, создать новый decision суперсидирующий windows-system-proxy-over-tun.
