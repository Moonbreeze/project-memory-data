---
date: 2026-03-12
project: ai-inst
topic: agent-skills-standard
source: imported
status: active
---
# Provider Note

## Overview

Открытый стандарт Agent Skills (agentskills.io) — формат SKILL.md с YAML frontmatter для навыков AI-агентов. Поддерживается Claude Code, Codex, Cursor, Roo Code, Windsurf.

## Constraints

- SKILL.md обязателен, остальные файлы опциональны
- name: lowercase + hyphens, макс 64 символа
- Платформо-специфичные поля (disable-model-invocation, user-invocable, allowed-tools, context, allow_implicit_invocation) — не стандартизированы

## Guidance

- Пути навыков по платформам: .claude/skills/ (Claude Code, Cursor, Windsurf), .agents/skills/ (Codex, Cursor, Roo, Windsurf)
- ai-inst копирует в оба пути для полного покрытия
- Содержимое SKILL.md копируется as-is, ai-inst не интерпретирует платформо-специфичные поля
- Frontmatter поля name и description используются для индекса навыков в целевых файлах
