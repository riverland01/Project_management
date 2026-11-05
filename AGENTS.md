# AGENTS.md

## Purpose

This workspace is a Markdown-first project management system for multiple long-running projects. It is designed to be readable and maintainable by humans, Codex, Claude Code, and other agentic tools.

Use this file for global working rules. Project-specific context belongs inside each project folder.

## Workspace Map

Before working, orient yourself using:

- `STATUS.md` - current portfolio-level status
- `INDEX.md` - map of active projects and important folders
- `glossary.md` - workspace-wide terms, acronyms, aliases, and phrase meanings
- `dependencies/active.md` - current cross-project dependencies
- `templates/` - reusable Markdown templates for common workspace files

Projects live in:

```text
projects/
```

Each project should usually contain:

```text
README.md
STATUS.md
TASKS.md
INDEX.md
glossary.md
dependencies.md
```

## Context Loading Order

When starting work:

1. Read root `STATUS.md`.
2. Read root `INDEX.md`.
3. Read root `dependencies/active.md` when work may affect multiple projects.
4. Read root `glossary.md` when terminology, acronyms, aliases, or phrase meanings matter.
5. Identify the relevant project.
6. Read the project's `STATUS.md`, `TASKS.md`, and `INDEX.md`.
7. Read the project's `glossary.md` when terminology, acronyms, aliases, or phrase meanings matter.
8. Read indexed contact/stakeholder registers when identity, roles, responsibilities, or approval authority matter.
9. Read deeper files only when the task requires them.

Prefer loading short current-state files before historical folders.

When resuming unfinished work, follow `maintenance/handoff-policy.md` and locate the applicable workstream's handoff through the relevant `INDEX.md`.

## Templates

Use the Markdown templates in `templates/` when creating new workspace-level files, project-level files, or cross-project dependency files.

High-priority templates include:

- `templates/workspace-README.md`
- `templates/workspace-STATUS.md`
- `templates/workspace-INDEX.md`
- `templates/workspace-glossary.md`
- `templates/project-README.md`
- `templates/project-STATUS.md`
- `templates/project-TASKS.md`
- `templates/project-INDEX.md`
- `templates/project-glossary.md`
- `templates/project-dependencies.md`
- `templates/workspace-contacts.md`
- `templates/project-stakeholders.md`
- `templates/dependencies-active.md`
- `templates/dependencies-dependency-map.md`

Ingestion templates live in `templates/ingestion/`:

- `templates/ingestion/meeting-note.md`
- `templates/ingestion/project-initiation.md`
- `templates/ingestion/email-thread.md`
- `templates/ingestion/ppt-deck.md`
- `templates/ingestion/source-summary.md`
- `templates/ingestion/decision-record.md`
- `templates/ingestion/blocker-record.md`
- `templates/ingestion/feedback-record.md`
- `templates/ingestion/role-change-record.md`

Reporting templates live in `templates/reporting/`:

- `templates/reporting/project-status-report.md`
- `templates/reporting/portfolio-status-report.md`
- `templates/reporting/dashboard.md`
- `templates/reporting/cross-project-kanban.md`
- `templates/reporting/cross-project-gantt.md`
- `templates/reporting/project-kanban.md`
- `templates/reporting/project-gantt.md`
- `templates/reporting/roadmap.md`
- `templates/reporting/milestones.md`
- `templates/reporting/risks.md`
- `templates/reporting/open-questions.md`
- `templates/reporting/lint-report.md`
- `templates/reporting/handoff.md`

When copying a template, replace placeholders, remove sections that do not apply, and keep current-state files concise. If an existing file is missing important sections from its template, update it gently without rewriting unrelated content.

## Interaction Modes

Users will usually interact with this workspace in one of two modes.

### 1. Ingesting New Material

The user may provide a file, pasted text, meeting note, project initiation form, email thread, PDF, Word document, PowerPoint deck, Outlook email, or other source material and ask the agent to ingest it.

When ingesting material:

1. Identify the relevant project or projects.
2. If the project is unclear, infer from the content when reasonable; otherwise ask a concise clarification.
3. Place or reference the source material in the most appropriate project folder.
4. Extract only the project-management-relevant information.
5. Update the relevant current-state Markdown files.
6. Append detailed historical information to the appropriate log folder.
7. Note any new dependencies, blockers, decisions, risks, open questions, sources, or follow-up tasks.

Use `templates/ingestion/` when creating ingestion summaries, meeting notes, decision records, blocker records, or feedback records. For flexible sources such as email threads and PowerPoint decks, use the closest template as a guide rather than a rigid form. Keep source-specific context in a flexible notes section when the material does not fit neatly into standard headings.

Use these destinations by default:

- Meeting notes: `projects/<project>/docs/meeting-notes/`
- Project initiation forms: `projects/<project>/docs/project-brief.md` or `projects/<project>/planning/`
- Email threads: `projects/<project>/docs/meeting-notes/` or `projects/<project>/project-log/feedback/`
- Decisions: `projects/<project>/project-log/decisions/`
- Blockers: `projects/<project>/project-log/blockers/`
- Feedback: `projects/<project>/project-log/feedback/`
- References and source material: `projects/<project>/decision-sources/`
- Analysis decks and outputs: `projects/<project>/analysis/`
- Deliverable drafts or finals: `projects/<project>/deliverables/`

When updating Markdown after ingestion:

- Update `STATUS.md` if the current project state changed.
- Update `TASKS.md` if there are new, completed, changed, or blocked tasks.
- Update `INDEX.md` if new important files or folders were added.
- Update `glossary.md` only if the material introduces or clarifies a term, acronym, alias, or phrase meaning; put operational updates in status, task, dependency, or log files.
- Update `dependencies.md` if the material introduces or changes dependencies.
- Update canonical contact/stakeholder registers and append dated role-change records when assignments change; follow People And Roles below.
- Update root `STATUS.md`, root `INDEX.md`, or `dependencies/` only if the information affects multiple projects or portfolio-level tracking.
- Update root `glossary.md` only if terminology applies across multiple projects or the whole workspace.

Preserve the original source file where possible. Do not copy long source content into status files; summarize the operational implications and link to the stored source or detailed note.

### 2. Querying Project Status

The user may ask for the current status of one or more projects, a portfolio summary, blockers, upcoming tasks, dependencies, risks, or a progress report.

When answering status queries:

1. Read root `STATUS.md` and `INDEX.md`.
2. Identify the requested project or project set.
3. Read each relevant project's `STATUS.md`, `TASKS.md`, `INDEX.md`, and `dependencies.md`.
4. Read root or project `glossary.md` when the question depends on terminology, acronyms, aliases, or phrase meanings.
5. Read indexed role registers for current assignments or dated records for historical assignments when roles matter; read other deeper files only when needed.
6. Summarize the current state clearly and distinguish facts from assumptions.
7. Mention stale, missing, or contradictory project files if they affect confidence.

Use `templates/reporting/` when creating formal status reports, dashboards, roadmaps, milestone summaries, risk summaries, open-question lists, Kanban views, or Gantt views. Treat reporting files as summaries or display layers; do not let them replace canonical task, status, dependency, or decision files.

For project-level summaries, include when relevant:

- Current objective
- Latest status
- Active tasks
- Recent changes
- Blockers
- Risks
- Open questions
- Upcoming milestones
- Dependencies
- Recommended next actions

For portfolio-level summaries, include when relevant:

- Overall status
- Projects on track
- Projects at risk
- Cross-project dependencies
- Shared blockers
- Near-term priorities
- Decisions needed from the user

Prefer concise summaries with links to source Markdown files. Do not over-read historical folders unless the user asks for background, audit trail, or detailed chronology.

## Workspace Lint

For workspace health checks, follow `maintenance/lint-sop.md`. It defines a manual structural and judgment review, finding triage, exceptions, and reporting. Use `templates/reporting/lint-report.md` for saved runs. Automated commands are proposed separately in the SOP and are not installed yet.

## Checkpoints And Handoff

Follow `maintenance/handoff-policy.md` for ingestion checkpoints, long conversations, transfers, and resumption. Use `templates/reporting/handoff.md` for full handoffs. Keep project state in canonical files and continuation details in linked, dated records.

## Current State vs History

Use this rule:

```text
Status, task, dependency, and role registers answer what is true now.
Indexes provide navigation; glossaries define terms without carrying status.
Logs and dated records preserve history; a register in a folder can still hold current state.
```

Keep these files short and current:

- root `STATUS.md`
- root `INDEX.md`
- project `STATUS.md`
- project `TASKS.md`
- project `INDEX.md`
- project `dependencies.md`

Keep root and project `glossary.md` files concise as dictionaries. Update them when meanings change, not when project progress changes.

Append or archive detailed history in:

- `project-log/changelog/`
- `project-log/decisions/`
- `project-log/blockers/`
- `project-log/feedback/`
- `docs/meeting-notes/`
- `analysis/notes/`
- `decision-sources/`

## Task Management

Use each project's `TASKS.md` as the canonical task list.

Visual files under `views/` are display layers only. Do not treat them as the source of truth unless a project explicitly says otherwise.

When updating tasks:

- Keep active and near-future tasks visible.
- Move completed or obsolete details into the appropriate log or archive.
- Do not backfill every historical task unless asked.

## Dependencies

Use project-level `dependencies.md` for dependencies local to one project.

Use the root `dependencies/` folder for cross-project dependencies:

- `dependencies/active.md`
- `dependencies/dependency-map.md`
- `dependencies/by-project/`

When a task affects another project, update both the local project dependency file and the relevant cross-project dependency view.

## Glossaries

Use root `glossary.md` for workspace-wide terms, acronyms, aliases, and phrases that have the same meaning across projects.

Use project-level `glossary.md` for terminology that is specific to one project.

Glossaries are dictionaries. They answer "What does this term mean?" and do not carry project or portfolio status.

When ingesting or updating material:

- Include only the term, acronym expansion, synonyms or aliases, concise definition, and optional stable usage clarification or definition source.
- Add or revise an entry only when terminology is introduced, clarified, or redefined. A progress update alone is not a glossary change.
- Exclude current progress, task completion, owners or assignments, due dates, milestone outcomes, blockers, risks, dependency state, approval state, next actions, and decision history. A term such as "Blocked" may be defined generically; do not record which project is blocked.
- Put current state in `STATUS.md`, actions in `TASKS.md`, dependencies in dependency files, and decisions or detailed history in the appropriate project log. Use `INDEX.md` for navigation.
- For mixed content, keep only the definition in the glossary and route operational information to its canonical file, preserving the source or history link. Do not duplicate the operational information in both places.
- Do not duplicate project-specific definitions in the root glossary unless they apply across the workspace.

Example: "Validation: checking a deliverable against agreed requirements" is a definition. "Validation is complete; review is due Friday" belongs in status and task files. A glossary's `Last updated:` date describes dictionary maintenance only; it is not a project status date.

## People And Roles

Keep identity, current assignments, and assignment history separate:

- **Glossary:** names, initials, aliases, and stable identity disambiguation only when useful for interpreting material. Define role meanings generically; do not attach current or former role assignments to a person's entry.
- **Organizational roles:** `shared/contacts.md` is the canonical register for affiliations and titles that need tracking. Create it from `templates/workspace-contacts.md` on first use and link it from root `INDEX.md`. Do not copy its title fields into each project.
- **Project roles:** `projects/<project>/docs/stakeholders.md` is the canonical register for project roles, responsibilities, and approval authority. Use `templates/project-stakeholders.md`; project READMEs link to it instead of maintaining another role table.
- **Role history:** use `templates/ingestion/role-change-record.md`. Project assignment changes go in `projects/<project>/project-log/changelog/YYYY-MM-DD-role-change-<person>.md`; organizational changes go in `shared/role-changes/YYYY-MM-DD-<person>.md`. Filenames use the recorded date; add a numeric suffix for collisions. Create shared folders only when needed. For a change affecting both scopes, keep one primary record linked from both registers and affected project notes.

Use a consistent full name with a stable disambiguator when names collide. Initials alone or a changing role title are not sufficient identity. No mandatory person-ID scheme is required.

When ingesting a role change:

1. Preserve the source and establish the person, organization/project scope, previous and new assignment, effective date, and recorded date. Keep unknown values explicit. Record initial assignments too; previous assignment may be unknown or not applicable.
2. Append a dated change record with evidence and register links. Separate confirmed changes from proposals or conflicting claims; do not overwrite an established assignment on ambiguous evidence.
3. Update the current register when the change takes effect. Keep confirmed future changes in a scheduled section with evidence, an effective date, and a follow-up task; do not present them as current. If evidence confirms a change is already in force but its start date is unknown, update current state with `Unknown` as the effective date.
4. Keep one current row per person, role, and scope; concurrent roles can have separate rows. Remove ended assignments from current rows after preserving them in history. Record a vacancy or unknown successor where the responsibility still exists.
5. Review affected tasks, dependencies, handovers, and approval responsibilities. Reassign only where evidence supports it; otherwise capture a follow-up task or open question. An organizational title change does not itself prove a project-role or task-owner change.
6. Link the change record from the register's history section and any relevant project index. Keep history as links rather than old assignments in current rows. Review only projects affected by a shared organizational change.

`Effective from` describes when an assignment applies; `Recorded` describes when it was entered here. Neither is inferred from ingestion or file-modification dates. Preserve original meeting notes and source documents with the roles reported at that time. Append later corrections with source pointers rather than rewriting history. Answer current-role questions from registers and historical-role questions from dated records and sources; note stale or conflicting evidence.

These registers are optional beyond the six-file minimum project overlay. Existing projects can retain a useful register at another path if their `INDEX.md` identifies it as canonical. Avoid duplicating it.

## Decision Sources

Use `decision-sources/` for references that shape project decisions, including papers, websites, internal docs, datasets, and stakeholder notes.

Keep `decision-sources/active.md` short. Move older or less relevant material to `decision-sources/archived.md`.

## Existing Project Migration

For existing projects, do not reorganize old files unless requested.

First add or update the minimum overlay:

```text
README.md
STATUS.md
TASKS.md
INDEX.md
glossary.md
dependencies.md
```

Use `INDEX.md` to describe legacy folders and active files. Add deeper folders only when they become useful.

## Update Rules

When making project-management updates:

- Preserve existing structure and naming unless there is a clear reason to change it.
- Keep current-state files concise.
- Put detailed rationale, meeting notes, decisions, blockers, and feedback into the relevant folder.
- Prefer links to detailed files instead of copying long content into status files.
- Do not create bureaucracy for its own sake.

## Agent Collaboration Notes

When working in this workspace:

- Explain significant changes briefly.
- Ask before large restructures.
- Avoid duplicating instructions between `AGENTS.md` and `CLAUDE.md`.
- Treat `CLAUDE.md` as a bridge that points Claude Code back to this file.
- If project-specific instructions conflict with this file, follow the project-specific instructions for that project.
