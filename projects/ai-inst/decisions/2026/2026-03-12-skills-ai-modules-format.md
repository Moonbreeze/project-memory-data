---
date: 2026-03-12
project: ai-inst
topic: skills-ai-modules-format
source: imported
status: active
---
# Decision

## Context

Нужно расширить формат .ai-modules для указания навыков проекта, сохраняя обратную совместимость с существующими файлами.

## Decision

Расширить .ai-modules секцией [skills]. Строки до [skills] — модули (как сейчас). Строки после [skills] — навыки. targets: может быть в любом месте. Комментарии и пустые строки игнорируются. parse_ai_modules возвращает три переменные: TARGETS, MODULES, SKILLS.

## Consequences

- Обратная совместимость: файл без [skills] работает как раньше
- project add-skill создаёт секцию [skills] если её нет
- project rm-skill удаляет имя из секции [skills]
