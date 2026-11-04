# Workspace Glossary

Last updated: 2026-11-04

Use this dictionary for terms, acronyms, aliases, and phrases that have the same meaning across the workspace. Include definitions and stable usage clarifications only; keep project status in the appropriate status, task, dependency, or log files.

## Terms

| Term | Also Known As | Meaning | Usage / Definition Source |
| --- | --- | --- | --- |
| Project current-state files | State files | Files describing current project state, actions, and dependencies: `STATUS.md`, `TASKS.md`, and `dependencies.md`. | Distinct from navigation and dictionary files. |
| Project overlay | Overlay files, minimum overlay | The core project management and reference files added to a project: `README.md`, `STATUS.md`, `TASKS.md`, `INDEX.md`, `glossary.md`, and `dependencies.md`. | An overlay can describe an existing project without reorganizing its legacy folders. |
| Glossary | Dictionary, terminology reference | A collection of terms, acronym expansions, aliases, and definitions. | Describes meanings without carrying project or portfolio status. |
| Decision sources | Sources, references | Materials that shape project decisions, such as papers, websites, internal documents, datasets, and stakeholder notes. | Stored in `decision-sources/`. |
| Display layer | View, visual view | A generated or maintained representation of project state, such as Kanban, Gantt, dashboard, or timeline files. | Canonical task state remains in `TASKS.md`. |
| Cross-project dependency | Portfolio dependency | A dependency where one project, owner, or workstream affects another project. | Tracked in `dependencies/`. |

## Scope

- Put workspace-wide terms here.
- Put project-specific terminology in `projects/<project>/glossary.md`.
