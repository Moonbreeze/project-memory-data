---
date: 2026-03-12
project: ai-inst
topic: skills-architecture
source: imported
status: active
---
# Decision

## Context

Контекст агента разрастается с увеличением количества модулей. Нужен механизм инструкций, загружаемых по запросу (on-demand), а не всегда присутствующих в контексте. Стандарт Agent Skills (agentskills.io) поддерживается Claude Code, Codex, Cursor, Roo Code, Windsurf.

## Decision

Добавить систему навыков (skills) в ai-inst. Навыки хранятся в rules-репо (~/.ai-instructions/skills/<name>/SKILL.md), конфигурируются в секции [skills] файла .ai-modules, при build копируются в .claude/skills/ и .agents/skills/ проекта. Формат — стандарт Agent Skills: директория с SKILL.md (YAML frontmatter + markdown) и опциональными поддиректориями (scripts/, references/, examples/, assets/). Содержимое копируется as-is, ai-inst не интерпретирует платформо-специфичные поля frontmatter.

## Consequences

- Новые CLI-команды: skill (list/new/edit/show/rm), project add-skill/rm-skill
- Расширение parse_ai_modules для секции [skills]
- Build копирует навыки в два пути: .claude/skills/ и .agents/skills/
- Build генерирует индекс навыков (description из frontmatter) в целевых файлах
- Build обновляет .gitignore для сгенерированных директорий навыков
- MCP-сервер получает новые tools: list_skills, read_skill, create_skill, update_skill, delete_skill, add_project_skill, remove_project_skill
- Формат .ai-modules обратно совместим — файл без [skills] работает как раньше
- repo init создаёт skills/ наряду с modules/
