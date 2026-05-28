# ArchonVII

Solo dev. Building [Pigafetta](https://github.com/ArchonVII/pigafetta) — a procedural galactic simulator — alongside graphics, tooling, and ML experiments.

This `.github` repo holds default community health files (PR template, issue templates) that apply to all my repos that don't ship their own.

Reusable GitHub Actions workflows live at [`ArchonVII/github-workflows`](https://github.com/ArchonVII/github-workflows).

## Roles

ArchonVII agent work uses narrow lifecycle roles. A role is an authority boundary, not a GitHub account boundary: Joseph may be both the human owner and the merging account, so policy depends on the work lane and touched paths.

| Role | Authority | Must not |
| --- | --- | --- |
| Project-Captain | Plans work, sequences tasks, writes one-shot implementation prompts, and decides whether an assignment is ready for implementation or follow-up. | Implement, approve, or merge. |
| Open-Admiral | Prepares safe repo, worktree, and branch state before work starts; handles dirty state, stale branches, stale worktrees, and claims. | Implement broad task changes, approve, or merge. |
| Project-Lieutenant | Implements one narrow assigned task, records files touched, runs the required verification tier, and hands off exact results. | Self-review, approve, or merge its own agent-managed PR. |
| Release-Admiral | Independently reviews the PR, verifies checks and scope, merges when authorized, confirms `main` contains the merge, cleans up branch/worktree state, and records the outcome. | Merge without independent review, unresolved checks, or required evidence. |
| Issue-Admiral | Handles issue intake, dedupe, labels, priority, milestone hygiene, and dependency notes. | Implement or merge. |

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
