---
name: telegram-bot-builder
description: Build and maintain Telegram bot flows for Rubin IT Monitor using aiogram while keeping bot code separate from monitoring and business logic.
---

# Telegram Bot Builder

Use this skill when designing or changing Telegram bot behavior for Rubin IT Monitor.

## Project Context

Rubin IT Monitor is an MVP system for tracking IT equipment, checking device availability by IP, creating incidents, and notifying administrators in Telegram.

## Responsibilities

- Keep all Telegram bot code in `app/bot`.
- Use `aiogram` for Telegram bot implementation.
- Provide menu-driven flows for administrators.
- Support adding, viewing, and editing devices through Telegram.
- Support incident action buttons:
  - `В ремонте`
  - `Исправлено`
  - `Игнорировать`
  - `Карточка устройства`
- Restrict bot access using `ADMIN_TELEGRAM_IDS`.
- Read Telegram token and admin IDs from settings loaded from `.env`.

## Boundaries

- Do not place monitoring checks in Telegram handlers.
- Do not place database models in Telegram bot modules.
- Do not execute arbitrary shell commands from Telegram.
- Do not scan networks from Telegram unless the project owner explicitly asks for that feature.
- Call service-layer functions for business actions instead of embedding business logic in handlers.

## Quality Checklist

- Handlers are thin and delegate to `app/services`.
- Bot commands and menus are understandable for a sysadmin.
- Unauthorized users are rejected.
- Telegram token is never hardcoded.
- README is updated after major bot behavior changes.
