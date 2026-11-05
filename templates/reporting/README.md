# Reporting Templates

Use these templates when creating project status reports, portfolio summaries, dashboards, or visual project-management views.

Reporting templates should summarize current state clearly and link back to source Markdown files. They should not become the canonical source of tasks, dependencies, or decisions.

## Templates

- `project-status-report.md`
- `portfolio-status-report.md`
- `dashboard.md`
- `cross-project-kanban.md`
- `cross-project-gantt.md`
- `project-kanban.md`
- `project-gantt.md`
- `roadmap.md`
- `milestones.md`
- `risks.md`
- `open-questions.md`
- `lint-report.md` - workspace or project health review; procedure in `maintenance/lint-sop.md`
- `handoff.md` - continuation note; active policy in `maintenance/handoff-policy.md`

## Reporting Rules

- Prefer facts from `STATUS.md`, `TASKS.md`, `INDEX.md`, and `dependencies.md`.
- Distinguish confirmed facts from assumptions or stale information.
- Keep summaries concise and actionable.
- Carry source tags beside decision-bearing claims under [Claim Sources And Attribution](../../maintenance/claim-sources.md), including certainty and author where relevant. Preserve provenance when summarizing; missing certainty is not confirmation.
- Keep project Recent Progress summaries to 5 dated entries with tags and a history link; do not rewrite finalized historical reports.
- Treat `views/` files as display layers, not the source of truth.

