# AGENTS.md

## Project
Rubin IT Monitor — MVP-система учёта и мониторинга техники с Telegram-уведомлениями для задач сисадмина.

## Goal
Создать приложение, которое хранит список техники, проверяет доступность устройств по IP, фиксирует проблемы и отправляет уведомления администратору в Telegram.

## Stack
- Python 3.11+
- FastAPI
- aiogram
- SQLAlchemy
- SQLite for MVP
- APScheduler
- pydantic-settings
- pytest
- ruff
- black

## MVP Features
1. Хранение техники в базе данных.
2. Telegram-бот с меню.
3. Добавление, просмотр и изменение техники.
4. Ping-проверка устройств из базы.
5. Автоматическая проверка каждые 5 минут.
6. Создание incident, если устройство недоступно.
7. Telegram-уведомление при новой проблеме.
8. Не спамить повторными уведомлениями, если проблема уже активна.
9. Уведомление о восстановлении, если устройство снова отвечает.
10. Кнопки: В ремонте, Исправлено, Игнорировать, Карточка устройства.

## Architecture Rules
- Keep bot logic in app/bot.
- Keep monitoring logic in app/monitoring.
- Keep database models in app/db.
- Keep business logic in app/services.
- Keep FastAPI routes thin.
- Do not mix Telegram handlers with monitoring code.
- Use SQLite for MVP, but keep code ready for PostgreSQL later.

## Security Rules
- Never hardcode Telegram bot token.
- Use .env and .env.example.
- Restrict bot access by ADMIN_TELEGRAM_IDS.
- Do not allow arbitrary shell commands from Telegram.
- Do not scan whole network ranges unless explicitly asked.
- Only check devices already added to the database.
- Do not store passwords in the database.

## Quality Rules
- Add tests for incident logic.
- Add tests for monitoring rules.
- Run ruff, black, and pytest before finishing.
- Update README after major changes.
