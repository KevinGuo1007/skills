# Project Instructions

This repository distributes reusable agent skills grouped by purpose. Follow
[README.md](README.md) for the collection layout and usage.

## Editing skills

- Keep each skill self-contained under `skills/<purpose>/<skill-name>/`. Resource
  links must resolve from the file that contains them and survive installation
  outside this repository.
- Treat instructions in the distributed skills as product content. Editing a
  skill does not activate its workflow in this repository.
- Changes to skill behavior require updating the relevant instructions and
  resources together. Adding or moving a skill also requires updating the root
  and group indexes and `.claude-plugin/plugin.json` skill paths.
- Verify changed frontmatter, local links, and referenced resources. For plugin
  metadata changes, run `claude plugin validate .` and
  `claude plugin validate .claude-plugin/plugin.json` when Claude Code is available;
  otherwise report the validation gap.

## Commit rules

Before drafting, reviewing, or creating a commit, read
[docs/commit-conventions.md](docs/commit-conventions.md). It is the single source
of truth for commit formatting and scope. Commit messages use English and
Conventional Commits.
