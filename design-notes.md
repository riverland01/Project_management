# Project Management Structure Design Notes

## Purpose

This workspace structure is designed for managing multiple long-running projects with Markdown files that are readable by humans, Codex, Claude Code, and other agentic coding or writing tools. It can be used to start new projects or added as an overlay on top of projects that are already running.

The structure balances four goals:

- Keep current context easy for an AI agent to load.
- Avoid giant Markdown files that clog the context window.
- Support multiple projects with cross-project dependencies.
- Stay compatible with Markdown-based project management views such as Kanban boards, Gantt charts, and timelines.

## Target Structure

The full target structure is:

```text
workspace-root/
  README.md
  AGENTS.md
  CLAUDE.md
  INDEX.md
  STATUS.md

  views/
    dashboard.md
    cross-project-kanban.md
    cross-project-gantt.md

  dependencies/
    README.md
    active.md
    dependency-map.md
    by-project/
      project-a.md
      project-b.md
    archived/

  shared/
    styleguide.md
    glossary.md
    contacts.md
    reusable-prompts.md

  templates/
    README.md
    workspace-README.md
    workspace-STATUS.md
    workspace-INDEX.md
    project-README.md
    project-STATUS.md
    project-TASKS.md
    project-INDEX.md
    project-dependencies.md
    dependencies-active.md
    dependencies-dependency-map.md
    ingestion/
      README.md
      meeting-note.md
      project-initiation.md
      email-thread.md
      ppt-deck.md
      source-summary.md
      decision-record.md
      blocker-record.md
      feedback-record.md
    reporting/
      README.md
      project-status-report.md
      portfolio-status-report.md
      dashboard.md
      cross-project-kanban.md
      cross-project-gantt.md
      project-kanban.md
      project-gantt.md
      roadmap.md
      milestones.md
      risks.md
      open-questions.md
    project-template/
      README.md
      STATUS.md
      TASKS.md
      INDEX.md
      dependencies.md
      planning/
      docs/
      project-log/
      decision-sources/
      deliverables/
      analysis/
      views/

  projects/
    project-a/
      README.md
      STATUS.md
      TASKS.md
      INDEX.md
      dependencies.md

      views/
        kanban.md
        gantt.md
        timeline.markwhen

      planning/
        roadmap.md
        milestones.md
        risks.md
        open-questions.md

      docs/
        project-brief.md
        meeting-notes/
          README.md
        reviews/
          README.md

      project-log/
        changelog/
          README.md
        decisions/
          README.md
        blockers/
          README.md
          active.md
          resolved/
        feedback/
          README.md
          active.md
          archived/

      decision-sources/
        README.md
        active.md
        papers.md
        websites.md
        internal-docs.md
        datasets.md
        archived.md

      deliverables/
        drafts/
        final/
        archived/

      analysis/
        README.md
        decks/
        notes/
          README.md
        outputs/

    project-b/
      README.md
      STATUS.md
      TASKS.md
      INDEX.md
      dependencies.md
      views/
      planning/
      docs/
      project-log/
      decision-sources/
      deliverables/
      analysis/
```

The current scaffold includes the required root files, `dependencies/`, `projects/`, `templates/`, and `templates/project-template/`. Workspace-level `views/` and `shared/` are intentionally deferred until they become useful.

## Why This Structure

The starting idea came from a Markdown-first project memory workflow: keep project instructions, tasks, decisions, blockers, schedules, sources, and review history in plain Markdown so both humans and agents can inspect and update the project state.

We adapted that idea for Codex and Claude Code by separating agent instructions into:

- `AGENTS.md` for general agent instructions.
- `CLAUDE.md` as a Claude Code bridge that points to `AGENTS.md`.

This avoids duplicating instructions while keeping the workspace compatible with Claude Code's expected `CLAUDE.md` convention.

## Multi-Project Design

Because the workspace may contain many projects, project-specific state lives under `projects/`.

Top-level files describe the whole workspace:

- `README.md` explains the workspace.
- `INDEX.md` maps active projects and important folders.
- `STATUS.md` summarizes the current portfolio-level situation.
- `AGENTS.md` gives global working rules.

Each project gets its own local state:

- `README.md` for project overview.
- `STATUS.md` for current project state.
- `TASKS.md` for active and near-future tasks.
- `INDEX.md` for project navigation.
- `dependencies.md` for local dependency notes.

This lets Codex load only the current project files instead of scanning every project.

## Context Control

Long-running projects can produce very long files. The structure avoids that by keeping root and project-level Markdown files short.

Short current-state files:

- `STATUS.md`
- `TASKS.md`
- `INDEX.md`

Historical or detailed material is split into folders:

- `project-log/changelog/`
- `project-log/decisions/`
- `project-log/blockers/`
- `project-log/feedback/`
- `docs/meeting-notes/`
- `analysis/notes/`

The rule is:

```text
Root files answer what is true now.
Folder files preserve what happened over time.
```

## Existing Project Migration

For projects that are already running, the structure should be added gradually. The first goal is to describe the current project clearly, not to reorganize every old file.

Start by adding the minimum overlay files inside the existing project folder:

```text
README.md
STATUS.md
TASKS.md
INDEX.md
dependencies.md
```

Use `INDEX.md` to map the current folder layout, including older folders and active working files. This lets Codex understand the project without needing the existing files to be moved immediately.

Example:

```markdown
# Project Index

## Current Working Files
- `slides/client-review-v3.pptx`
- `analysis/current-model.xlsx`

## Legacy Folders
- `archive/` - completed earlier work
- `old-drafts/` - previous drafts, use only for reference

## Project Management
- `STATUS.md`
- `TASKS.md`
- `project-log/decisions/`
```

After the overlay is useful, add the deeper folders only where they help:

```text
project-log/
decision-sources/
views/
analysis/
```

Do not backfill every historical task or decision. Capture only the decisions, blockers, sources, and dependencies that still affect the project.

## Decision Sources

The original `sources/` folder was renamed to `decision-sources/` to make its purpose clearer.

This folder contains the references used for decision making, such as:

- papers
- websites
- internal documents
- datasets
- stakeholder notes

`decision-sources/active.md` should stay short. It contains only the sources currently shaping open decisions.

Older or less relevant sources move to:

```text
decision-sources/archived.md
```

## Cross-Project Dependencies

The workspace includes a top-level `dependencies/` folder because projects may depend on each other.

Important files:

- `dependencies/active.md` lists current cross-project dependencies.
- `dependencies/dependency-map.md` can show the overall relationship map, often with Mermaid.
- `dependencies/by-project/` stores one dependency view per project.
- `dependencies/archived/` stores resolved or obsolete cross-project dependency records.
- `projects/*/dependencies.md` gives the local dependency view inside each project.

This makes dependencies visible without forcing every project to load every other project.

## Analysis Work

Each project includes an `analysis/` folder because some projects may need analysis PowerPoints or supporting outputs.

Typical contents:

- `analysis/decks/` for PowerPoint analysis decks.
- `analysis/notes/` for analysis notes, split by date or topic.
- `analysis/outputs/` for exported charts, PDFs, tables, or other generated material.

## Visual Project Management Views

The `views/` folders are optional display layers for project-management software.

Workspace-level examples:

- `views/dashboard.md`
- `views/cross-project-kanban.md`
- `views/cross-project-gantt.md`

Project-level examples:

- `projects/project-a/views/kanban.md`
- `projects/project-a/views/gantt.md`
- `projects/project-a/views/timeline.markwhen`

These files can support Markdown-based tools such as Obsidian Kanban, Mermaid Gantt diagrams, Markwhen timelines, or later export into GitHub Issues and Projects.

The canonical task data should remain in `TASKS.md`. The `views/` files are for visual organization.

## High-Priority Templates

The `templates/` folder contains reusable Markdown templates for files that agents and humans will create or update repeatedly.

High-priority templates:

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

Use these templates when creating new workspace-level files, new project overlay files, or cross-project dependency files. When applying a template to an existing project, preserve useful existing content and add only the sections that improve clarity.

For a brand-new project, prefer copying `templates/project-template/` to `projects/<project-name>/` and then replacing placeholders. The scaffold includes the standard current-state files plus lightweight README or placeholder files in nested folders so the intended structure is trackable and self-documenting.

## Ingestion Templates

The `templates/ingestion/` folder contains templates for turning incoming source material into project memory.

Ingestion templates:

- `templates/ingestion/meeting-note.md`
- `templates/ingestion/project-initiation.md`
- `templates/ingestion/email-thread.md`
- `templates/ingestion/ppt-deck.md`
- `templates/ingestion/source-summary.md`
- `templates/ingestion/decision-record.md`
- `templates/ingestion/blocker-record.md`
- `templates/ingestion/feedback-record.md`

These templates should be used when a user provides meeting notes, project initiation material, email threads, PowerPoint decks, PDFs, Word documents, or other source files for ingestion.

Some source types, especially email threads and PowerPoint decks, may not fit cleanly into a fixed structure. For those sources, use the closest ingestion template as a guide rather than a rigid form. Preserve the original file where possible, summarize the operational implications, and keep source-specific context in a flexible notes section.

## Reporting Templates

The `templates/reporting/` folder contains templates for project status reports, portfolio summaries, dashboards, visual views, roadmaps, milestone summaries, risk summaries, and open-question lists.

Reporting templates:

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

Use these templates when a user asks for the status of one or more projects, a portfolio report, a dashboard, or an optional visual project-management view. Reporting files should summarize and link back to source Markdown files. They should not become the canonical source for tasks, dependencies, decisions, or project state.

## Operating Principle

Use this structure as a memory system, not as bureaucracy.

Start each project with the minimum useful files:

```text
README.md
STATUS.md
TASKS.md
INDEX.md
dependencies.md
```

Then add detail folders only when the project needs them.

The intended workflow is:

1. Check workspace `STATUS.md` and `INDEX.md`.
2. Check `dependencies/active.md` when work may affect multiple projects.
3. Open the relevant project folder.
4. Read that project's `STATUS.md`, `TASKS.md`, and `INDEX.md`.
5. Read the project's `dependencies.md` when dependencies may affect the answer or update.
6. Load deeper files only when the task requires them.
7. Update current-state files and append detailed history to the appropriate folder.
