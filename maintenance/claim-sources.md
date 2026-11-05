# Claim Sources And Attribution

Last updated: 2026-11-05

## Scope

Attach source tags to new or substantively changed claims that affect project decisions: status, ownership, organizational/project roles, approval authority, scope, commitments, target dates, milestone outcomes, blockers, dependencies, risks, and material estimates. Apply this in canonical files, role registers, reports, views, handoffs, and substantive status answers. Navigation, headings, generic definitions, and clearly marked template examples do not need claim tags.

Written chat instructions are written evidence: capture their message/context in a note when needed. Use verbal tags for spoken statements, not merely because a message appeared in a conversation.

A source tag identifies evidence; it does not itself prove the claim. Read the source and check its date, scope, and authority. Do not invent a source, speaker, author, approval, or certainty to complete a tag. Capture available evidence in a dated note when the claim otherwise exists only in a conversation, file extraction, or agent analysis. Preserve source originals where possible.

## Tag Syntax

Minimal forms:

```text
[src: <note filename>]
[verbal: <name>, <date>]
```

Optional fields go inside the same tag, separated by semicolons:

```text
[src: <note filename>; certainty: Confirmed; by: <claim author>]
[verbal: <speaker>, YYYY-MM-DD; certainty: Proposed; by: <claim author>]
```

Use `certainty:` and `by:` consistently. The certainty values are `Confirmed`, `Proposed`, `Pending`, `Open`, and `Estimate`. If certainty is omitted, it is unspecified, not implicitly Confirmed. Label uncertainty explicitly, especially for proposals, missing confirmation, unresolved questions, and estimates. Include the claim author when known and useful; use `Unknown` rather than guessing if attribution matters but is unavailable.

`by:` identifies who made the claim, not automatically the task owner, approver, note writer, or person entering the data. In a verbal tag, the named speaker is the default claimant; use `by:` only when a different attribution needs explanation. An agent's analysis is attributed to that agent rather than to a stakeholder.

Dates use `YYYY-MM-DD`. A verbal date is when the statement was made, not when it was entered. Use `Unknown` for an unavailable speaker or date, mark certainty Open where that gap prevents reliance, and retain a follow-up question. Never substitute today's date for an unknown statement date.

## Locating Written Sources

Prefer a note path relative to the file carrying the claim, optionally followed by `#heading`. A bare filename is acceptable if it resolves in the same folder or uniquely among the project's indexed sources/notes. Use a relative path when ambiguous or crossing projects; a shared source must be reachable through the root or relevant project index. Source tags are plain text, not Markdown links, so check their targets separately.

Cite the dated note or record that contains the evidence. That note must identify its original source, author or speaker when known, source date, recorded date, and relevant excerpt or faithful summary. For a PDF, email, spreadsheet, website, or other external material, retain or reference the original and identify the page, message, range, section, or version supporting the claim. Use the source-summary template or `templates/ingestion/claim-note.md` when a small standalone note is sufficient.

For a new standalone project claim note, use `projects/<project>/decision-sources/YYYY-MM-DD-claim-<topic>.md` with the recorded date and a numeric suffix for collisions. Existing meeting, decision, analysis, or role-change records are preferred when they already hold the evidence. Link important notes from the project index or source register. Workspace-only claim notes can use `maintenance/notes/YYYY-MM-DD-claim-<topic>.md`, linked from the root index; create the folder only when needed.

A report may cite a canonical file if the supporting claim there retains a traceable source chain. Do not let status files cite each other in a circle. A note that merely repeats an assertion without identifying its origin is not independent corroboration. Creating a note from verbal evidence does not turn the underlying evidence into written confirmation: preserve its speaker, statement date, and verbal nature. A claim may carry both a written-note tag and its verbal tag.

## Certainty Meanings

| Label | Meaning |
| --- | --- |
| Confirmed | Supported by identified evidence appropriate to the claim's scope and authority. Confirmation that someone reported a fact is not independent verification of that fact, and does not imply approval unless approval is evidenced. |
| Proposed | A suggestion or intended assignment/decision that has not been accepted. |
| Pending | A specific check, answer, acceptance, or approval is awaited. State what is pending and link a follow-up where needed. |
| Open | Unresolved, conflicting, unknown, or lacking adequate evidence. Keep the gap visible. |
| Estimate | An approximation, forecast, or inference based on stated assumptions or calculations. The source note records the basis and author. |

These labels describe the claim, not task workflow. A task may be In progress while its due date is an Estimate and its owner is Confirmed. A verbal claim can be Confirmed when the statement itself is adequate authority, such as a person accepting an assignment; it does not automatically confirm a reported outcome.

## Attaching Tags

Put tags next to the exact claim they support. If status, owner, and deadline have different evidence or certainty, tag them separately. A table's Source Tags cell can cover the row only when the evidence and attribution support every material claim in that row; otherwise label the tags by field or place them in the individual cells. A report-wide source list alone does not attribute individual claims.

Illustrative examples only; the people and filenames below are fictional:

```text
Owner: Alex [verbal: Alex, 2026-11-05; certainty: Confirmed]
Target: 2026-12-01 [src: docs/meeting-notes/planning-note.md; certainty: Estimate; by: Alex]
Status: At risk [src: project-log/changelog/review-note.md; certainty: Confirmed; by: Project lead]
Proposed reviewer: Sam [src: docs/meeting-notes/planning-note.md; certainty: Proposed; by: Alex]
```

If there is no usable source, keep the claim or field explicitly unresolved, for example `Owner: Unknown [certainty: Open]`. A certainty-only tag is a gap marker, not a source. Create a follow-up when the missing fact affects action. An agent recommendation may be recorded in a dated analysis note with its assumptions and attribution; never present it as a stakeholder commitment.

Preserve the original claim, author, and source when copying a supported claim into a summary. Record derived assessments in a note explaining the reasoning and inputs. When new evidence changes a claim, update current state and append a dated correction with links to the superseded evidence. Do not rewrite finalized source notes, old reports, or historical meeting records just to make them match current state.

## Adoption And Review

Apply this to new claims and claims touched during normal updates. When reviewing a material legacy claim, trace it if possible; otherwise flag the gap and keep it Open or Pending as appropriate. Do not backfill fabricated tags or rewrite all history. There are no active projects to migrate at adoption.

Use the manual lint procedure to check source-target resolution, evidence support, attribution, certainty, and traceability. This policy does not install an automated checker or verifier.
