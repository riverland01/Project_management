# Lint Log

Newest first. `RULES` records a procedure/design change; `RUN` points to a saved review. These entries record maintenance, not project task state.

When the live log exceeds 30 entries, move the oldest entries into dated Markdown files under `maintenance/lint-log-archive/` and retain links here. Create that folder only on the first rollover.

## Recent

- [2026-11-05] RULES workspace - implemented organizational/project role registers and dated role-change templates, with effective/recorded dates, future-change handling, evidence, and downstream follow-up. Replaced scaffold README role tables with a canonical register link; shared registers remain optional until real use. Scoped consistency and reference checks only; no full lint run - [rules](../AGENTS.md#people-and-roles), [design](../design-notes.md#people-and-role-tracking).

- [2026-11-04] RULES workspace - aligned glossary design, agent instructions, templates, ingestion and handoff guidance with dictionary-only use; clarified state versus reference files and added a glossary-content check to J06. Reviewed the existing dictionary and sample scaffold; no active project status needed migration. Scoped verification only; no full lint run - [design](../design-notes.md#glossaries), [rules](../AGENTS.md#glossaries).

- [2026-11-03] RUN workspace baseline - partial review, two design warnings and one informational observation; no active projects to validate - [report](lint-reports/2026-11-03.md).
- [2026-11-03] RULES workspace - designed a manual lint procedure, exception registry, report template, and optional automation contract from the trial and wiki references; no checker or scheduler installed - [SOP](lint-sop.md).
