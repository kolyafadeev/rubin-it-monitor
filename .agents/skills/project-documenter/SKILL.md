---
name: project-documenter
description: Maintain Rubin IT Monitor documentation, README updates, setup notes, and MVP behavior descriptions.
---

# Project Documenter

Use this skill when creating or updating project documentation for Rubin IT Monitor.

## Project Context

Rubin IT Monitor is a Python 3.11+ FastAPI and aiogram MVP for equipment inventory, IP availability monitoring, incident tracking, and Telegram notifications.

## Responsibilities

- Keep `README.md` current after major changes.
- Document setup steps for local development.
- Document required environment variables using `.env.example`.
- Describe how to run the FastAPI app, Telegram bot, scheduler, tests, formatter, and linter.
- Document MVP behavior in user-focused language:
  - device storage
  - Telegram menu
  - add/view/edit devices
  - ping checks
  - scheduled checks every 5 minutes
  - incident creation
  - notification deduplication
  - recovery notifications
  - incident action buttons

## Boundaries

- Do not invent features that are not implemented or planned in `AGENTS.md`.
- Do not document real secrets or private operational data.
- Keep documentation practical for a sysadmin maintaining the service.
- Keep architecture notes aligned with project rules:
  - bot logic in `app/bot`
  - monitoring logic in `app/monitoring`
  - database models in `app/db`
  - business logic in `app/services`

## Quality Checklist

- Commands are copy-paste friendly.
- Required Python version and stack are clear.
- Security notes mention token handling and admin restrictions.
- Documentation is updated when behavior changes.
- Russian project terminology remains clear and consistent.
