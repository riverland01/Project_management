# CLAUDE.md

This workspace uses `AGENTS.md` as the canonical instruction file for agent behavior.

Claude Code should read and follow:

- `AGENTS.md` - global workspace and project-management rules
- `STATUS.md` - portfolio-level current state, if present
- `INDEX.md` - workspace map, if present

When working inside a project, Claude Code should then read:

- `projects/<project>/STATUS.md`
- `projects/<project>/TASKS.md`
- `projects/<project>/INDEX.md`
- `projects/<project>/dependencies.md`

Use templates from:

- `templates/` for workspace, project, and dependency files
- `templates/ingestion/` for source ingestion notes and records
- `templates/reporting/` for status reports and visual reporting views

Do not duplicate global instructions here. If guidance changes, update `AGENTS.md` first and keep this file as a lightweight bridge.
