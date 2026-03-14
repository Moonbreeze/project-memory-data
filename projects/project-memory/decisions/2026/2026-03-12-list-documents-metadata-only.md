---
date: 2026-03-12
project: project-memory
topic: list-documents-metadata-only
source: user
status: active
---
# Decision

## Context

list_documents возвращает полные тела всех документов. При росте количества документов это неоправданно забивает контекст агента. При этом search_documents уже возвращает только excerpt, а для чтения конкретного документа есть read_document.

## Decision

Изменить list_documents: по умолчанию возвращать только metadata (path, type, project, topic, date) без body. Добавить опциональный параметр include_body для полного вывода, когда это действительно нужно. Паттерн list/get — list обзорный, read_document для содержимого.

## Consequences

- list_documents перестаёт забивать контекст агента полными телами документов
- Агенты используют list для обзора, read_document для чтения конкретных документов
- Обратная совместимость: вызовы без include_body получают облегчённый ответ — потребители, полагающиеся на body в list, должны быть обновлены
- search_documents остаётся без изменений — уже возвращает excerpt
