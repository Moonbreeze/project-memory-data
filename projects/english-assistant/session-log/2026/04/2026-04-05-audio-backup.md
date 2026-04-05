---
date: 2026-04-05
recorded_at: 2026-04-05T13:00:29.518Z
project: english-assistant
topic: audio-backup
source: agent
status: active
---
# Session Note

## Summary

Расширен deploy/backup.sh аудио-бэкапом: tar.gz архив из локальной директории или через docker cp, независимая ротация, upload hook для обоих файлов. Обновлена документация, добавлены автотесты.

## Actions

- Добавлены функции backup_audio_local, backup_audio_container, rotate_audio_backups в deploy/backup.sh
- Добавлены переменные DEPLOY_AUDIO_BACKUP_ENABLED, DEPLOY_AUDIO_DIR, DEPLOY_AUDIO_BACKUP_RETENTION
- Upload hook вызывается отдельно для DB и аудио с DEPLOY_CREATED_BACKUP_PATH
- Обновлена секция Backup в deploy/README.md с описанием audio backup
- Добавлены 5 vitest-тестов: создание архива, ротация, отключение, пустая директория, upload обоих файлов

## Follow-up

- Проверить audio backup через docker cp на реальном VPS (work-item backup-production-rollout)
