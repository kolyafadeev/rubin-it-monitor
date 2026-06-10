---
name: monitoring-engine
description: Design monitoring checks, scheduling, incident transitions, and notification triggers for Rubin IT Monitor.
---

# Monitoring Engine

Use this skill when designing or changing device availability checks and incident rules for Rubin IT Monitor.

## Project Context

Rubin IT Monitor checks only devices already stored in the database, detects availability problems by IP, creates incidents, and sends Telegram notifications for new problems and recoveries.

## Responsibilities

- Keep monitoring code in `app/monitoring`.
- Use `APScheduler` for scheduled checks.
- Run automatic checks every 5 minutes for MVP.
- Check device availability by IP using a safe ping strategy.
- Create an incident when a device becomes unavailable.
- Avoid duplicate notifications while a problem is already active.
- Send a recovery notification when the device answers again.
- Call notification services instead of importing Telegram handlers.

## Boundaries

- Do not scan whole network ranges unless explicitly requested by the project owner.
- Only check devices already added to the database.
- Do not mix Telegram handlers with monitoring code.
- Do not store credentials or device passwords.
- Keep PostgreSQL migration in mind, but use SQLite for MVP.

## Quality Checklist

- Monitoring rules are covered by tests.
- Incident creation and recovery paths are covered by tests.
- Repeated failures do not spam Telegram notifications.
- Monitoring logic is deterministic enough to test without real network dependencies.
- `ruff`, `black`, and `pytest` pass before finishing implementation work.
