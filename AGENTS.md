# AGENTS.md

## Purpose

This workspace is a Markdown-first project management system for multiple long-running projects. It is designed to be readable and maintainable by humans, Codex, Claude Code, and other agentic tools.

Use this file for global working rules. Project-specific context belongs inside each project folder.

## Workspace Map

Before working, orient yourself using:

- `STATUS.md` - current portfolio-level status
- `INDEX.md` - map of active projects and important folders
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
dependencies.md
```

## Context Loading Order

When starting work:

1. Read root `STATUS.md`.
2. Read root `INDEX.md`.
3. Identify the relevant project.
4. Read the project's `STATUS.md`, `TASKS.md`, and `INDEX.md`.
5. Read deeper files only when the task requires them.

Prefer loading short current-state files before historical folders.

## Templates

Use the Markdown templates in `templates/` when creating new workspace-level files, project-level files, or cross-project dependency files.

High-priority templates include:

- `templates/workspace-README.md`
- `templates/workspace-STATUS.md`
- `templates/workspace-INDEX.md`
- `templates/project-README.md`
- `templates/project-STATUS.md`
- `templates/project-TASKS.md`
- `templates/project-INDEX.md`
- `templates/project-dependencies.md`
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
- Update `dependencies.md` if the material introduces or changes dependencies.
- Update root `STATUS.md`, root `INDEX.md`, or `dependencies/` only if the information affects multiple projects or portfolio-level tracking.

Preserve the original source file where possible. Do not copy long source content into status files; summarize the operational implications and link to the stored source or detailed note.

### 2. Querying Project Status

The user may ask for the current status of one or more projects, a portfolio summary, blockers, upcoming tasks, dependencies, risks, or a progress report.

When answering status queries:

1. Read root `STATUS.md` and `INDEX.md`.
2. Identify the requested project or project set.
3. Read each relevant project's `STATUS.md`, `TASKS.md`, `INDEX.md`, and `dependencies.md`.
4. Read deeper files only when needed to answer the question.
5. Summarize the current state clearly and distinguish facts from assumptions.
6. Mention stale, missing, or contradictory project files if they affect confidence.

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

## Current State vs History

Use this rule:

```text
Root and project-level files answer what is true now.
Folder files preserve what happened over time.
```

Keep these files short and current:

- root `STATUS.md`
- root `INDEX.md`
- project `STATUS.md`
- project `TASKS.md`
- project `INDEX.md`
- project `dependencies.md`

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
