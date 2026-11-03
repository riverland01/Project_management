# Ingestion Templates

Use these templates when ingesting source material into a project folder.

The goal is to preserve the source, extract project-management-relevant information, and update the current-state Markdown files without forcing every source into the same shape.

For flexible sources such as email threads and PowerPoint decks, keep the sections that fit, rename sections when useful, and add source-specific notes where needed.

## Templates

- `meeting-note.md`
- `project-initiation.md`
- `email-thread.md`
- `ppt-deck.md`
- `source-summary.md`
- `decision-record.md`
- `blocker-record.md`
- `feedback-record.md`

## Common Ingestion Rules

- Preserve or link to the original source file where possible.
- Capture the source date, ingestion date, project, and source location.
- Extract tasks, decisions, blockers, risks, dependencies, and open questions.
- Update current-state files only with concise operational summaries.
- Put detailed historical notes in the relevant project-log or docs folder.
- Follow [the handoff policy](../../maintenance/handoff-policy.md) at ingestion batch boundaries and when unfinished work needs a full handoff.

