---
name: security-reviewer
description: Review Rubin IT Monitor changes for token safety, Telegram access control, network-scan limits, and safe operations.
---

# Security Reviewer

Use this skill when reviewing or implementing changes that affect security, credentials, Telegram access, network checks, or operational safety.

## Project Context

Rubin IT Monitor is used for sysadmin workflows and Telegram alerts. It must protect bot credentials, limit access to approved administrators, and avoid risky network behavior.

## Responsibilities

- Ensure Telegram bot token is never hardcoded.
- Ensure `.env` is used for secrets and `.env.example` documents required variables.
- Ensure Telegram access is restricted by `ADMIN_TELEGRAM_IDS`.
- Ensure Telegram users cannot run arbitrary shell commands.
- Ensure monitoring checks only devices stored in the database.
- Ensure network range scanning is absent unless explicitly requested.
- Ensure device passwords are not stored in the database.

## Review Checklist

- No secrets are committed.
- `.env` is ignored by Git.
- `.env.example` contains placeholder values only.
- Bot authorization is checked before privileged actions.
- Monitoring cannot be abused as a broad scanner.
- Error messages do not leak secrets.
- Logs do not print Telegram token or sensitive settings.

## Quality Expectations

- Security concerns should be reported with concrete file and line references.
- Prefer small fixes that preserve the current architecture.
- If a change introduces new risk, recommend a safer project-aligned alternative.
