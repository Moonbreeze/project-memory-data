---
date: 2026-03-21
recorded_at: 2026-03-21T00:00:00.000Z
project: mastihin
topic: security-baseline
source: user
status: active
---
# Decision

## Context

Определение минимальных требований безопасности для MVP. Платформа с загрузкой изображений и UGC — повышенные риски XSS и вредоносных файлов.

## Decision

Обязательно с первого коммита: XSS (санитизация ввода, class-validator, strip HTML), CSP (helmet, разрешить изображения только со своего S3, запрет inline-скриптов), загрузка файлов (проверка magic bytes, лимит 15MB, ресайз через sharp пересоздаёт файл и убивает payload в метаданных, UUID-имена, приватный бакет + presigned URLs), SQL injection (параметризованные запросы через ORM), CORS (строго origin mastihin.ru), rate limiting (Nginx + NestJS throttler на login/register и общий). Позже: CSRF, логирование подозрительной активности, 2FA для модератора.

## Consequences

- Ресайз через sharp служит двойной цели: оптимизация + безопасность
- Presigned URLs усложняют клиент, но защищают бакет
- Helmet + CSP могут ломать сторонние скрипты — нужно тестировать

## Stable Guidance Review

- Outcome: bootstrap-exempt
- Summary: Bootstrap-style decision write where no prior stable-guidance surface existed yet.
- Note: Первые решения проекта.
