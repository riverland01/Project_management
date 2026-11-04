# Project Management Workspace

## Purpose

This workspace is a Markdown-first project management system for tracking multiple long-running projects, their current state, tasks, dependencies, source material, and decision history.

## Active Projects

- No active projects have been added yet.

## Workspace Files

- `STATUS.md` - current portfolio-level status
- `INDEX.md` - map of active projects and important folders
- `glossary.md` - shared terms, acronyms, aliases, and phrase meanings
- `AGENTS.md` - global agent working rules
- `CLAUDE.md` - Claude Code bridge

## Key Folders

- `projects/` - project-specific state and working files
- `dependencies/` - cross-project dependencies
- `templates/` - reusable Markdown templates
- `maintenance/` - lint and handoff policies, exceptions, and review history

## Operating Notes

- Start each new project with the minimum overlay: `README.md`, `STATUS.md`, `TASKS.md`, `INDEX.md`, `glossary.md`, and `dependencies.md`.
- Keep root and project current-state files concise. Glossaries are dictionaries for meanings and aliases; keep progress, actions, and other operational state in their canonical files.
- Put detailed history, source material, decisions, blockers, and feedback in the appropriate project folders.
- Use [the lint procedure](maintenance/lint-sop.md) for workspace health checks. It is agent-assisted; no automated checker is installed yet.
- Follow [the handoff policy](maintenance/handoff-policy.md) to checkpoint ingestion batches and preserve continuation context when work transfers or a long conversation ends with unfinished work.
