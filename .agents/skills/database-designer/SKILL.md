---
name: database-designer
description: Design SQLAlchemy models, persistence boundaries, and SQLite-first schema decisions for Rubin IT Monitor.
---

# Database Designer

Use this skill when designing or changing database models and persistence logic for Rubin IT Monitor.

## Project Context

Rubin IT Monitor stores IT equipment, device status, and incidents. SQLite is used for the MVP, but the code should stay ready for PostgreSQL later.

## Responsibilities

- Keep database models in `app/db`.
- Use SQLAlchemy for models and persistence.
- Store devices with enough fields for inventory and monitoring:
  - name
  - IP address
  - device type or category
  - location or owner when useful
  - active/enabled flag
  - current status
- Store incidents with enough fields to support lifecycle logic:
  - related device
  - status
  - first detected time
  - last checked time
  - resolved time
  - notification state when needed
- Keep database access behind service or repository-style functions when it simplifies callers.

## Boundaries

- Do not put Telegram handlers in database modules.
- Do not put monitoring scheduler code in database modules.
- Do not store passwords in the database.
- Do not hardcode environment-specific database paths.
- Avoid SQLite-only assumptions where PostgreSQL-compatible SQLAlchemy patterns are practical.

## Quality Checklist

- Models are simple and explicit.
- Relationships support incident and device workflows.
- Database setup can run from a clean environment.
- Tests can use an isolated temporary SQLite database.
- README documents basic setup after major schema changes.
