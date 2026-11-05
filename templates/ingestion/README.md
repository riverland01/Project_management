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
- `role-change-record.md`
- `claim-note.md` - small dated record for a claim, its origin, author, evidence, and uncertainty

## Common Ingestion Rules

- Preserve or link to the original source file where possible.
- Capture the source date, ingestion date, project, and source location.
- Apply [Claim Sources And Attribution](../../maintenance/claim-sources.md): attach written/verbal tags to important claims, preserve speaker/date for verbal statements, distinguish claim author from recorder, and label uncertainty. Reuse adequate source notes or create a dated claim note; never manufacture corroboration.
- Keep project Recent Changes and Done Recently to 5 entries each; preserve overflow evidence in dated history before trimming.
- Extract tasks, decisions, blockers, risks, dependencies, and open questions.
- For role changes, separate organizational titles from project responsibilities. Update canonical registers, preserve dated records with effective and recorded dates, and review affected tasks and approvals. Follow [People And Roles](../../AGENTS.md#people-and-roles).
- Roles reported in source summaries describe that source at its date; preserve them when later assignments change.
- Update current-state files only with concise operational summaries.
- Update glossaries only for terms and meanings; route progress, actions, and other operational state to status, task, dependency, or log files.
- Put detailed historical notes in the relevant project-log or docs folder.
- Follow [the handoff policy](../../maintenance/handoff-policy.md) at ingestion batch boundaries and when unfinished work needs a full handoff.

