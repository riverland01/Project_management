# Handoff Policy

Last updated: 2026-11-03
Status: Active; approved by the user on 2026-11-03.

## Purpose

Make work resumable after a long conversation, a large ingestion, an interruption, or a change of person or agent. A reader should be able to identify the current objective, trust the saved project state, and take the next action without replaying the conversation.

The principle is: **save project truth as work proceeds; hand off only the context needed to resume it.** A handoff is a dated continuation note, not another canonical task list or a transcript.

This policy uses the workspace's current-state/history distinction and [lint procedure](lint-sop.md). It does not require a new mandatory overlay file, an automatic chat reset, a scheduler, or a script.

## Two Levels

| Level | When to use it | What to save |
| --- | --- | --- |
| Checkpoint | At each ingestion batch boundary or meaningful work boundary | Updated canonical files, source progress, and any unresolved next step. Usually a short entry in the existing ingestion note or changelog, plus a concise chat update. |
| Full handoff | Work is transferring, or a long/complex conversation is ending with unfinished work | A dated note with read order, objective, decisions, source cursor, changes, verification, open questions, and the next action. |

A completed, simple task needs its normal completion summary and current-state updates. It does not need a separate handoff file just because the chat was long. A status query alone does not require project files to be rewritten.

## Triggers

### Checkpoint Required

- After each completed ingestion batch. Choose a batch small enough that its processing state can be reconstructed; define the included sources at the start.
- When a decision or user correction changes project state or the approach. Save it before moving to unrelated work.
- Before switching away from unfinished work to a different project or workstream.
- At a safe boundary when context pressure is visible or the agent can no longer reliably distinguish processed material from pending material.

Do not wait until the end of a large batch to save everything. Persist each completed source summary and its supported updates as work proceeds. A batch checkpoint reconciles that saved work; it is not the first durable write.

### Full Handoff Required

- The user asks for a handoff or intends to continue the work in another chat, tool, or with another person.
- Work is being transferred to another agent or person.
- A long or complex conversation is ending while material remains unprocessed, updates remain unapplied, or decisions remain unresolved.
- A known context transition or interruption makes loss of working context likely. Save at the next safe point if possible; do not claim to detect every automatic compaction or unexpected shutdown.

Conversation length is a warning signal, not a reliable fixed message or token threshold. A checkpoint does not itself end the task or require a new chat. If the user asked for continued work, continue after saving unless a transfer, answer, or permission is actually needed.

## Checkpoint Procedure

1. **Reconcile current state.** Update only the affected `STATUS.md`, `TASKS.md`, `INDEX.md`, `glossary.md`, and dependency files under existing ingestion rules. Record important decisions and corrections in the appropriate project log. Keep root changes limited to portfolio or cross-project implications.
2. **Record source progress.** In the source/ingestion note, identify what is stored, read or extracted, reviewed, and applied. These are separate states. Record failures, exclusions, and unverified content.
3. **Save the cursor.** For incomplete work, name the exact next file, page range, slide, worksheet, email message, section, or pending update. Mark what was already applied so a resuming agent does not create duplicate tasks or records.
4. **Run a scoped check.** Check changed references, placeholders, task/status consistency, and any dependency endpoints touched. State the actual coverage using the lint SOP; do not imply a full workspace lint pass.
5. **Confirm briefly in chat.** State what was saved, what remains, and the next action. Do not wait for fresh approval for work already authorized.

If interrupted before reconciliation finishes, save an explicitly **partial** checkpoint with the missing steps. Never label a batch complete merely because all source files were copied or extracted.

## Full Handoff Contents

Use [the handoff template](../templates/reporting/handoff.md), removing sections that do not apply. Aim for about one page, expanding only when necessary to preserve a precise source cursor or critical constraint.

| Required content | What it must establish |
| --- | --- |
| Scope and snapshot | Project/workstream, date and timezone, objective, what the user requested, and whether work is complete, partial, or blocked |
| Read first | A short ordered set of links to the applicable instructions, canonical current-state files, and essential detailed notes |
| Decisions and corrections | Confirmed choices, latest user corrections, evidence pointers, and important rejected approaches whose rationale affects the next step; separate proposals and assumptions |
| Saved changes | Files created or updated, facts/tasks actually applied, and changes still drafted or unapplied |
| Ingestion progress | Source identity/location, processing stages, exact unfinished cursor, extraction/access limitations, and whether downstream updates were verified |
| Validation | Checks actually run, results, unresolved lint findings, and checks not run |
| Open work | Linked canonical task/decision IDs where available, missing facts, known blockers, and the exact next action |
| Working state | Git revision when available, relevant uncommitted work, and any running process or unsaved state; do not imply another agent inherits a live session |
| Resume instruction | A short instruction telling the next reader what to read, verify, and do first within the existing scope |

Record authorization precisely when relevant, with a pointer to the instruction or decision. A handoff cannot grant new permission, broaden the task, or turn a proposal into an approved decision. Preserve unknown owners and dates as unknown. Never include credentials or copy long source content into a handoff.

## Storage And Discovery

- **Project handoff:** `projects/<project>/project-log/changelog/YYYY-MM-DD-handoff-<workstream>.md`.
- **Workspace or multi-project handoff:** `maintenance/handoffs/YYYY-MM-DD-<workstream>.md`. Create this folder only when the first real handoff is needed. Link to the affected projects rather than duplicating their state.
- Use a short descriptive workstream slug and a numeric suffix if a filename would collide. Do not overwrite a different concurrent handoff.
- Add or replace a single current handoff link per active workstream in the relevant project's `INDEX.md`, or root `INDEX.md` for a workspace handoff. Old notes remain in history; do not accumulate all of them in the current index.
- Label the snapshot with its date and revision. Finalized handoffs preserve what was known then; later notes supersede them. Select the applicable workstream, not simply the newest file in the repository.

Do not add `HANDOFF.md` to every project or create an empty handoff folder in every scaffold. Existing source notes, project logs, indexes, and canonical tasks should carry most of the durable context.

## Resume Procedure

1. Follow `AGENTS.md` context-loading order. Locate the current handoff for the intended workstream through the relevant index.
2. Read the handoff and its essential pointers. Compare its snapshot against current project files, later decisions, and relevant working-tree changes before applying updates.
3. Treat a handoff as historical when later evidence changes the state. Do not roll canonical files back to match it. If current files conflict and evidence cannot resolve the conflict, state the uncertainty.
4. Confirm what was already stored, reviewed, and applied. Resume at the recorded cursor and avoid duplicating tasks, summaries, dependencies, or decision records.
5. Continue the recorded next action within the user's scope. Ask only for a missing fact, unresolved material choice, or authorization that is actually required; do not repeat a settled question just because the agent changed.
6. Update canonical files as work proceeds. When the workstream is finished, remove its current handoff pointer or mark it completed in the index; keep the dated note as history.

## Readiness Check

A full handoff is ready when another reader can answer these questions from the note and its links:

- What is the intended outcome, and what has the user actually decided?
- Which files describe current truth?
- What has already been applied, and what remains pending or unverified?
- Where exactly should work resume?
- What checks were completed, and what limitations remain?

Unfinished work and open findings are compatible with a good handoff if clearly recorded. An inaccessible essential source, missing cursor, unsaved change, or unresolved contradiction must be explicit; label the handoff partial when it prevents reliable continuation.

## Adoption And Review

Adopted with the user's approval on 2026-11-03. `AGENTS.md` points to this policy and lists the handoff template. Keep the detailed procedure here rather than duplicating it in `CLAUDE.md`. Apply the policy to new work without backfilling every historical conversation. Review its usefulness after the first substantial ingestion and continuation, adjusting only if the evidence shows a gap.

The policy is implemented through workspace instructions and Markdown records. It does not depend on an automated trigger or move work to another chat on its own.
