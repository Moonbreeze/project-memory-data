---
date: 2026-10-08
recorded_at: 2026-10-08T06:10:12.168Z
project: vpn-reality
topic: relay-outage-direct-de-fallback
source: agent
status: active
---
# Verification Result

## Scope

Диагностика общего отказа relay и временный прямой VLESS Reality на DE:443.

## Steps

- До fallback: systemctl status показывает active x-ui, mtg и wg-quick@wg-mtg; ss показывает 8443 и приватный 10.66.0.2:3128.
- До fallback: curl к api4.ipify.org/api64.ipify.org возвращает 147.45.196.137 / 2a0f:cdc6:500:758::2; HTTPS www.cloudflare.com возвращает 200.
- До fallback: SSH и nc к relay 178.154.193.39:22/443/9443 завершаются таймаутом; ping relay и 10.66.0.1 имеет 100% потерь.
- Панель 3x-ui через loopback отвечает HTTP 200; пользователь выполнил административную настройку по инструкции для отдельного VLESS Reality Vision inbound DE:443.
- После настройки пользователь подтвердил: всё подключилось успешно.
- После подтверждения выполнен ss -lntu: появился LISTEN 147.45.196.137:443, backend MTProto по-прежнему слушает только 10.66.0.2:3128; listener 8443 сохранён.

## Result

Временный direct-DE доступ подтверждён сообщением пользователя и локальным listener на DE:443. Недоступность relay с DE подтверждена измерениями; авария Yandex Cloud известна со слов пользователя, не подтверждена независимым status API. Ограничения: агент не имеет sudo, не проверил live inbound key/SNI/flow, UFW правила и клиентский egress; отдельных результатов Telegram и проверки из мобильной сети пользователь не предоставил. Приватная привязка mtg backend сохранена. Восстановление relay и последующее удаление fallback остаются отдельным follow-up.
