# ArchonVII

Solo dev. Building [Pigafetta](https://github.com/ArchonVII/pigafetta) — a procedural galactic simulator — alongside graphics, tooling, and ML experiments.

This `.github` repo holds default community health files (PR template, issue templates) that apply to all my repos that don't ship their own.

Reusable GitHub Actions workflows live at [`ArchonVII/github-workflows`](https://github.com/ArchonVII/github-workflows).

## Roles

ArchonVII agent work uses narrow lifecycle roles. A role is an authority boundary, not a GitHub account boundary: Joseph may be both the human owner and the merging account, so policy depends on the work lane and touched paths.

A role name does not imply a repo-local command, script, workflow, or executable agent exists. Treat role names as authority and policy vocabulary unless the current repo explicitly documents an invocation.

| Role | Authority | Must not |
| --- | --- | --- |
| Project-Captain | Plans work, sequences tasks, writes one-shot implementation prompts, and decides whether an assignment is ready for implementation or follow-up. | Implement, approve, or merge. |
| Open-Admiral | Prepares safe repo, worktree, and branch state before work starts; handles dirty state, stale branches, stale worktrees, and claims. | Implement broad task changes, approve, or merge. |
| Project-Lieutenant | Implements one narrow assigned task, records files touched, runs the required verification tier, and hands off exact results. | Self-review, approve, or merge its own agent-managed PR. |
| Release-Admiral | Independently reviews the PR, verifies checks and scope, merges when authorized, confirms `main` contains the merge, cleans up branch/worktree state, and records the outcome. | Merge without independent review, unresolved checks, or required evidence. |
| Issue-Admiral | Handles issue intake, dedupe, labels, priority, milestone hygiene, and dependency notes. | Implement or merge. |

### Role Taxonomy

Use these categories when reading or extending ArchonVII process docs:

- **Authority role**: a human or agent responsibility boundary in the lifecycle.
- **Executable command/agent**: a repo-local script, workflow, skill, or named command that can be invoked.
- **PR marker/configuration signal**: text or configuration consumed by PR policy automation.
- **Future automation**: planned automation scope that is not a current repo-local command.

| Role/name | Taxonomy | Current meaning |
| --- | --- | --- |
| Project-Captain | Authority role. | Planning and assignment authority only. No org-level executable command is implied. |
| Open-Admiral | Authority role; possible future automation. | Repo/worktree opening authority. A repo may provide bootstrap helpers, but the role name itself is not an invocation. |
| Project-Lieutenant | Authority role; PR marker/configuration signal. | Implementation authority for one assigned task. In `github-workflows` PR policy, a PR body containing `Project-Lieutenant` or `LIEUTENANT_HANDOFF` is one signal that the PR is agent-managed. It does not satisfy independent review and does not name an executable command. |
| Release-Admiral | Authority role; PR marker/configuration signal; future automation. | Independent review and closeout authority. In `github-workflows` PR policy, `Release-Admiral: @reviewer-name` is a PR-body marker that can satisfy the non-author marker requirement when role separation is hard-enforced and `@reviewer-name` is not the PR author or a commit author. The marker is evidence for policy only; it does not merge, approve, or run a command. |
| Issue-Admiral | Authority role; future automation. | Issue-triage authority. The role may get standardized output or tooling later, but this document does not define an executable command. |

The reusable [`ArchonVII/github-workflows`](https://github.com/ArchonVII/github-workflows) role policy also treats an `agent/` branch name or `agent-managed` label as an agent-managed signal. Those signals classify the PR lane; they do not create role authority by themselves.

Related scope links:

- [ArchonVII/.github#16](https://github.com/ArchonVII/.github/issues/16) owns the Release-Admiral "finish it" runbook and any related closeout automation.
- [ArchonVII/.github#18](https://github.com/ArchonVII/.github/issues/18) owns the Issue-Admiral triage format, cadence, and pilot triage.
- [ArchonVII/github-workflows#35](https://github.com/ArchonVII/github-workflows/pull/35) documents reusable workflow accounting and role/script ownership gaps.
- [ArchonVII/archon-setup#63](https://github.com/ArchonVII/archon-setup/pull/63) records ecosystem setup status; it does not change this taxonomy.

## Lane Policy

### 1. Owner Maintenance Lane

Direct `main` maintenance is allowed only when all constraints are true:

- The change is add-only: no deletes and no renames of tracked files.
- Every path is in the safe set: `docs/research/**`, `docs/notes/**`, `docs/assets/**`, `**/*.{png,jpg,jpeg,gif,webp,svg}`, or `.changelog/**`.
- No path is in the unsafe set: `README.md`, `AGENTS.md`, `CLAUDE.md`, `GEMINI.md`, `.github/**`, `.githooks/**`, `.claude/**`, `.agent/schema/**`, `package*.json`, `src/**`, `scripts/**`, `docs/process/**`, or `docs/architecture/**`.
- No issue, PR, handoff, Release-Admiral, claim record, or full CI is required.
- Commit messages use lightweight owner scope, such as `docs(owner): ...` or `chore(owner): ...`; no issue reference is required.

Agents that find only add-only safe maintenance files should report `owner maintenance present, no action required` unless explicitly asked to commit them. If any unsafe file is present, stop and report the lane conflict.

### 2. Agent-Managed Code/Config PRs

Agent-managed implementation work that touches code, CI, hooks, policy, or agent-process files requires hard role separation:

- Project-Lieutenant performs the assigned implementation.
- The implementation agent cannot be the Release-Admiral for that same PR.
- Release-Admiral independently reviews, verifies, merges when authorized, confirms the merge is present on `main`, cleans up the branch/worktree, and records the outcome.

### 3. Global Default

Outside the owner-maintenance lane and protected agent-managed lanes, same-account authorship or merge identity is a soft warning by default. Do not enforce a universal `merged_by != commit_author` hard block unless protected paths or lane-specific rules require it.

## Dependabot Exception

Dependabot auto-merge is the explicit exception to the agent role-separation policy. The exception applies only to the repo's configured Dependabot automation and does not authorize agents to self-review or self-merge implementation PRs.

## Standard Agent Closeout

Every agent closeout or status update should include enough detail for the next authority to verify the lane:

```text
repo:
full_local_folder:
issue_ids:
pr_ids:
branch:
worktree:
verification:
  - command:
    result:
server_url:
remaining_follow_ups:
```
