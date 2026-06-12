# .github

User-level default community health files for repos under [@ArchonVII](https://github.com/ArchonVII).

Files in `.github/` here are picked up automatically by **any of my repos that does not ship its own copy**. A repo can always override by putting its own file in its own `.github/`.

## What this repo provides

| File                                         | Applies when a repo has no...                                 |
| -------------------------------------------- | ------------------------------------------------------------- |
| `.github/PULL_REQUEST_TEMPLATE.md`           | own `PULL_REQUEST_TEMPLATE.md`                                |
| `.github/ISSUE_TEMPLATE/task.yml`            | own task issue form                                           |
| `.github/ISSUE_TEMPLATE/bug.yml`             | own bug issue form                                            |
| `.github/ISSUE_TEMPLATE/feature_request.yml` | own feature request form                                      |
| `.github/ISSUE_TEMPLATE/chore.yml`           | own chore / tech-debt form                                    |
| `.github/ISSUE_TEMPLATE/documentation.yml`   | own documentation issue form                                  |
| `.github/ISSUE_TEMPLATE/prd.yml`             | own PRD (parent issue) form                                   |
| `.github/ISSUE_TEMPLATE/config.yml`          | own issue config (disables blank issues)                      |
| `.github/release.yml`                        | own release-notes generator config (categorizes PRs by label) |
| `SECURITY.md`                                | own security policy (shows "Report a vulnerability" banner)   |
| `profile/README.md`                          | public profile bio shown at https://github.com/ArchonVII      |

## Starting a new repo

See [`STARTER.md`](STARTER.md) for the canonical document-policy guide: when to add `README.md` / `CHANGELOG.md` / `TODO.md` / `ARCHITECTURE.md` / `AGENTS.md` / ADRs / `CHANGELOG` fragments, plus a setup checklist. Pair with [`ArchonVII/github-workflows`](https://github.com/ArchonVII/github-workflows) for the workflow side and [`ArchonVII/repo-template`](https://github.com/ArchonVII/repo-template) for clone-and-go scaffolding.

## Agent workflow policy

The public profile README is not an agent-policy source. It should stay focused
on the visible GitHub profile for `ArchonVII`.

Agent workflow rules belong in the active `AGENTS.md` instructions, this repo's
issue and PR templates, and the reusable workflow documentation in
[`ArchonVII/github-workflows`](https://github.com/ArchonVII/github-workflows).
Keep process-heavy role and lane guidance out of `profile/README.md` unless it
is directly relevant to the public profile.

## What this repo does NOT provide

- **`CODEOWNERS`** — must live in each repo's own `.github/` to be enforced; GitHub does not honor a default one here.
- **Workflows / Actions** — see [`ArchonVII/github-workflows`](https://github.com/ArchonVII/github-workflows) for reusable workflows you can call from any consumer repo.
- **Branch protection** — per-repo settings; not file-based.

## How GitHub resolves community health defaults

Order of precedence for a given repo:

1. Files in that repo's own `.github/` (or repo root).
2. Files in this `ArchonVII/.github` repository.

No CI, no installs, no opt-in. Just create the file here and any new repo inherits it.
