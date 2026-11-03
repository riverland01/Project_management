# Workspace Status

Last updated: 2026-11-03

## Overall Status

The workspace structure includes root current-state files, glossary support, dependency tracking, a project container, and a reusable project template scaffold. A manual lint procedure is available, and the checkpoint/handoff policy is active. No active projects have been added yet.

## Active Projects

| Project | Status | Current Focus | Risk Level | Next Milestone |
| --- | --- | --- | --- | --- |
| None yet | Not started | Add first project when available | Low | First project intake |

## Cross-Project Priorities

- Add active project folders under `projects/` as work begins.
- Keep `dependencies/active.md` updated when projects start depending on each other.

## Active Cross-Project Dependencies

- None currently tracked.

## Shared Blockers

- None currently tracked.

## Decisions Needed

- Decide the naming convention for project folders before adding the first project.

## Notes

- Use `templates/project-template/` when creating new project folders.
- Use root `glossary.md` for workspace-wide terminology and project `glossary.md` files for project-specific terms.
- Use [the handoff policy](maintenance/handoff-policy.md) for checkpoints and continuation, and [the lint procedure](maintenance/lint-sop.md) for scoped health checks. No automated checker or scheduler is installed.
