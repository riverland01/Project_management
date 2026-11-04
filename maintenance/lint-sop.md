# Workspace Lint Procedure

Last updated: 2026-11-04

## Purpose And Availability

Lint checks whether the workspace is safe to rely on: current files agree, references resolve, tasks and dependencies are traceable, and uncertain facts remain visible. Prioritize misleading project information over cosmetic Markdown issues.

This is a manual, agent-assisted procedure usable now. The check IDs below also specify candidates for future automation. There is currently **no lint script, automatic fix command, Git hook, CI job, or scheduled run** in this repository. A manual review must say which checks were actually completed.

`AGENTS.md` remains the authority for workspace rules. This SOP describes maintenance within those rules. It does not replace project-specific instructions or make every optional scaffold folder mandatory.

## Invocation And Triggers

Examples of requests a person can give an agent:

- "Lint the workspace; report findings only."
- "Lint projects/example-project after this ingestion; check its cross-project dependencies too."
- "Fix the evidence-backed findings in the latest lint report."

| Trigger | Recommended scope |
| --- | --- |
| Ingest or edit one project | Changed files, that project's current-state files, and affected dependency endpoints |
| Create a project | Its six overlay files and its root index/status entries; inspect copied template references |
| Bulk ingestion, rename, or change across projects | Whole workspace |
| Prepare a portfolio report or handoff | Portfolio files and included projects |
| Change templates or workspace rules | Design review plus one sample scaffold review; do not create a live project just to test a template |
| Periodic upkeep | Monthly when the workspace is in active use; run on request, without assuming a scheduler exists |

A quick check after a small edit may be summarized in chat. Use a saved report for a full pass, a handoff, or unresolved findings that need follow-up.

## Boundaries

- Start in report-only mode unless the request already authorizes fixes. Existing authorization covers routine, reversible corrections supported by workspace evidence; do not ask again for the same action.
- Never invent owners, dates, task outcomes, approvals, or dependency states. Missing information stays open and becomes a question.
- Change a `Last updated:` date only when the file was substantively updated or its current content was actually reviewed. A recent file timestamp or commit proves an edit, not that all claims were verified.
- Preserve stored source originals, quoted evidence, and historical records. Correct current summaries with a source pointer; record a later correction separately when history needs clarification.
- During a routine lint pass, report defects in instructions, templates, or lint rules as design proposals. Change them when the user's request covers that design work. Ask before a large restructure, as required by `AGENTS.md`.
- Keep unrelated user edits intact. Do not delete Git lock files, reset Git state, mass-normalize line endings, rename sources, or reorganize legacy folders to make lint pass.
- Views and lint reports summarize canonical files. They do not become a second task list or replace project decisions and dependencies.

## Procedure

### 1. Establish Scope And Baseline

Read root `STATUS.md` and `INDEX.md`, then applicable instructions, glossaries, and dependency files in the order in `AGENTS.md`. For a project run, read its `STATUS.md`, `TASKS.md`, `INDEX.md`, and `dependencies.md` before deeper material.

Record the review date in Asia/Singapore, scope, Git revision, existing uncommitted changes, and any unavailable material. Useful read-only commands from the workspace root are:

```powershell
git status --short
git rev-parse --short HEAD
rg --files -g '*.md' -g '!maintenance/lint-reports/**'
```

If Git is unavailable, continue a file review but mark Git-based checks unavailable. A lock's age alone does not prove it is abandoned; report a Git problem rather than removing a lock.

### 2. Run The Structural Checks

Work through Tier 1 for the selected scope. Inspect code fences, examples, and source quotations before declaring a defect. Record evidence as a path plus heading, line, or short excerpt. Distinguish absent files from optional future files.

### 3. Run The Judgment Checks

Work through Tier 2 for the same scope. Follow a decision or source pointer only when it can resolve a specific question. For cross-project dependencies, read both endpoints even on a project-scoped run; report any needed edits outside the authorized scope separately.

### 4. Triage Each Finding

| Disposition | Use when | Next step |
| --- | --- | --- |
| Fix | Evidence supports a local, reversible correction | Apply when fixes are authorized; otherwise propose file, change, and evidence |
| Ask | A fact, outcome, owner, or material choice is missing | State the precise question; keep the finding open |
| Design | The cause is a template, instruction, rule, or checker defect | Propose the smallest design change; implement only within authorized scope |
| Exception | The departure is intentional and understood | Record the narrow scope, rationale, owner, and review date in the exception registry |
| No defect | An example, quotation, planned path, or other false positive | Explain why; do not create an exception just to suppress a bad rule |

Severity and disposition are separate. A high-consequence finding may need an answer rather than an immediate fix. Order findings by impact on decisions, then by urgency.

### 5. Apply Authorized Fixes And Verify

Make the smallest supported edits. Recheck affected references and any mirrored dependency or portfolio entries. For a formatting-only change, `git diff --ignore-blank-lines -w` should show no new semantic difference attributable to that fix; compare against the preflight diff if the workspace was already dirty.

If a correction changes a recorded project fact, append a concise entry to that project's `project-log/changelog/` using the closest ingestion record template as a guide. Do not manufacture a project log for a workspace-only design change; record that in the maintenance log.

Do not clear a finding just because a file changed. Record the verification evidence or leave it open.

### 6. Report And Close

Use [the lint report template](../templates/reporting/lint-report.md). Save formal reports as `maintenance/lint-reports/YYYY-MM-DD.md`; use `-2`, `-3`, and so on for later runs on the same day. Append a pointer in [the lint log](lint-log.md). Finalized reports preserve what was known at the time; later runs record subsequent resolution.

Give every check a coverage result: **completed**, **partial**, **not run**, or **not applicable**, with a reason for the last three. A clean structural pass does not certify the judgment checks.

The scope is **clear** when all applicable checks were completed and no unresolved errors or warnings remain. It is **clear with exceptions** when that is true after valid exceptions are separated. Otherwise report **findings open** or **incomplete**, including any checks not run. Informational observations alone do not block a clear result.

## Scope And Severity

Review scope includes root `STATUS.md`, `INDEX.md`, `glossary.md`, dependency current files, and each real project's six overlay files. Glossaries are dictionary references within this scope, not project status files. Include active blocker/feedback registers when present. A folder under `templates/project-template/` is a template, not a real project.

- **Error:** a confirmed defect that breaks navigation or could materially misstate active project state.
- **Warning:** a probable defect, missing context, or maintenance risk needing review.
- **Info:** an observation or suggestion; no correction is implied.

Do not scan `.git/`, installed packages, caches, or binary attachments as Markdown. Inspect templates as designs: placeholders are expected there. Check history only when needed to investigate a current finding; quoted old paths, dates, and statuses are not current-state defects. Do not rewrite old lint reports to satisfy new rules.

## Tier 1: Structural Checks

These are manual checks today. Exact file/date checks are good automation candidates; ambiguous prose stays a warning for review.

| ID | Default severity | Check and limits |
| --- | --- | --- |
| S01 | Error | Required root navigation/state files exist. Each real project normally has `README.md`, `STATUS.md`, `TASKS.md`, `INDEX.md`, `glossary.md`, and `dependencies.md`; a missing overlay file is a warning until its migration or dormant status is understood. Optional deeper folders are not required. |
| S02 | Error | Explicit local Markdown links resolve to the intended file, folder, or supported heading anchor. Ignore fenced examples and external URLs. Missing local targets are errors; uncertain anchor-rendering behavior is a warning. Backticked paths are advisory evidence, not automatically links. |
| S03 | Warning | A document has a clear title, sensible heading hierarchy, readable lists, and consistent table columns. Ignore code fences, escaped pipes, and pipes inside inline code. Formatting becomes an error only if it loses or changes meaning. |
| S04 | Warning | A dated current-state or dictionary file has a real calendar date in `Last updated:` and no future review date. Cover the root/project status, index, glossary, task, and dependency files that use this field. Do not require dates on every README, source original, or historical note. |
| S05 | Warning | Active project `STATUS.md` or `TASKS.md` is more than 30 days old, or older than relevant newly ingested evidence. Age signals a review need, not proof the content is false. Paused/dormant projects and an empty workspace are reviewed in context. Record any threshold override. |
| S06 | Warning | A live copied template still has unfilled dates, option lists, author instructions, or empty operational fields. Inspect context: `TBD` may truthfully record an unknown. It remains a visible gap when action depends on it, rather than an invented value or automatic error. |
| S07 | Error | Each real project is reachable from root `INDEX.md` and represented in root `STATUS.md`, directly or through an explicit dormant/archived grouping. Empty-workspace rows are not projects. |
| S08 | Warning | Every active cross-project dependency is traceable in the root register and both projects' dependency files. Compare its identity, direction, status, and evidence, not exact wording. Confirmed status contradictions escalate to errors. No new ID convention is imposed. |
| S09 | Info | A current-state or dictionary file exceeds about 150 lines, completed tasks accumulate, or a log grows difficult to load. This is a review prompt, not a hard cap or permission to archive automatically. |
| S10 | Warning | Exception rows are complete, narrowly scoped, and within their review date. Expired rows stop suppressing findings; unused rows need review. |

Preserve existing LF or CRLF line endings. There is no repository line-ending policy today. Generic line-length rules, bare-URL bans, blanket trailing-space removal, and prose style preferences are outside this procedure; Markdown trailing spaces can encode a line break.

## Tier 2: Judgment Checks

| ID | Review | Evidence to compare |
| --- | --- | --- |
| J01 | Contradictions | Project status against tasks, active blockers, dependencies, and portfolio summaries. A serious blocker is a review trigger, not automatic proof the whole project is blocked. |
| J02 | Stale or superseded claims | Current summaries against the relevant newer decision, meeting note, changelog, or source summary. State what the newer evidence actually establishes. |
| J03 | Missing operational follow-up | Decisions, blockers, feedback, and source actions that should have a task, owner, resolution, or dependency record. Unknown owners remain unknown. |
| J04 | Overdue outcomes | Past milestone or task targets without a recorded outcome. Ask whether completed, delayed, cancelled, or still unknown; do not infer failure from the date alone. |
| J05 | Navigation and provenance | Important working files reachable through project indexes; claims and decisions traceable to stored sources or notes. Flag inaccessible evidence without altering originals. |
| J06 | Duplication and glossary drift | Conflicting definitions or rules; `CLAUDE.md` duplicating `AGENTS.md`; template copies drifting; views disagreeing with canonical tasks. Check that glossary entries contain meanings and stable usage or definition sources only. Flag progress, assignments, dates for work, blockers, approvals, dependency state, next actions, or decision history in a glossary; route these to canonical state files or logs. Generic definitions of status labels and dictionary maintenance dates are allowed. Similar wording alone is not a defect. |
| J07 | Current state versus history | Dated narrative and old completed work obscuring the next action. Recommend a minimal move with links, preserving evidence and existing legacy layout. |
| J08 | Design gaps and suggestions | Optional paths presented as existing files, unclear template guidance, or useful unanswered questions. Separate observed defects from suggestions. No new web research or project is automatically triggered. |

## Exceptions

Use [the exception registry](lint-exceptions.md). Each row has an ID, check ID, exact file or narrow folder, optional finding match, reason, owner, recorded date, and review-by date no more than six months after recording. A folder scope ends in `/`; it applies only beneath that folder. An exact file applies only to that file. An optional match narrows the specific finding, not every rule on the path.

An exception applies through its review date. On the next day it expires and the underlying finding becomes visible again. An accepted unknown outcome is still an open question, not an exception. Unsupported rationale or missing ownership leaves the row invalid. Do not copy the trial workspace's project-specific exceptions.

## Optional Automation Design

If requested, implement `scripts/lint.mjs` with a dependency-free supported Node runtime. The interface to implement is report-only by default, with `--project <slug>`, `--json`, `--today YYYY-MM-DD`, and `--stale-days <positive integer>`. These are proposed options, not working commands.

The checker should return 0 when it completes without unsuppressed errors, 1 when errors remain, and 2 for invalid options or a failed/incomplete scan. Warnings stay visible even with exit 0; this is a structural result, not the full SOP outcome. Validate dates and project slugs, reject unknown options and out-of-workspace paths, and report coverage and exceptions in JSON. Project scope must include required portfolio checks and affected dependency endpoints.

Start with S01, local-file targets in S02, S04-S07, and S10. Keep heading anchors, backticked paths, tables, placeholder detection, and dependency prose advisory until representative cases are verified. Do not claim to automate J01-J08. Ignore templates as live content and avoid following symlinks outside the workspace.

Before adoption, test missing targets versus planned/example paths, fenced code, inline-code and escaped table pipes, Windows paths, invalid/future dates, template versus live placeholders, dormant migrations, scoped dependencies, and expired exceptions. Test a seeded defect as well as a clean case. A future fixer needs separate authorization and verification; whitespace is not universally meaning-free in Markdown.

## Design Sources And Adaptation

Reviewed on 2026-11-03:

- Local trial reference: `D:/Repos/Proj_management_trial/maintenance/lint-sop.md`, its exception registry, log, two lint reports, and the checker interface. These are external references, not dependencies required to run this SOP.
- [Wiki operations](https://github.com/riverland01/general_wiki/blob/b3e00400e0415a4ed303ff181d70298de7167bb4/design/operations.md), especially Lint and Redesign: contradictions, stale claims, navigation, divergent duplication, and keeping design changes distinct from maintenance.
- [Wiki structure](https://github.com/riverland01/general_wiki/blob/b3e00400e0415a4ed303ff181d70298de7167bb4/design/structure.md): canonical sources, short navigation files, immutable originals, and concise logs.

Retained the two-tier review, evidence-based triage, scoped runs, reviewable exceptions, and small report/log structure. Adapted them to this workspace's optional folders, gradual migration, unstructured task/dependency prose, and existing authorization rules. Wiki-specific frontmatter, backlink schemas, concept promotion, blanket approval gates, and the trial's LF policy are not adopted. There is no design-domain precedence over `AGENTS.md` here.
