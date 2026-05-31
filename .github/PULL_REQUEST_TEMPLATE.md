<!--
  This template is the default for any repo under @ArchonVII that does not
  ship its own PULL_REQUEST_TEMPLATE.md.

  If your repo opts into the shared `pr-policy` or `repo-required-gate`
  reusable workflow from ArchonVII/github-workflows, non-draft PRs must
  satisfy the strict PR contract:

    1. Conventional Commit title
    2. `## Summary`
    3. `## Verification`
    4. `### Verification Notes`
    5. `## Docs / Changelog`
    6. Linked issue (`Closes #N`, `Fixes #N`, or `Refs #N`)
    7. No placeholder text
    8. Concrete checked verification evidence

  Doc-only PRs (every changed file is `.md`/`.txt`/an image/`.changelog/**`)
  skip the body ceremony.

  Tick a verification box `[x]` only after the command actually passed.
-->

## Summary

TODO: What changed and why?

## Verification

- [ ] TODO: Replace with an exact command, CI check, or manual smoke test.

  ```evidence
  command: TODO
  location: local
  result: TODO
  timestamp: TODO
  ```

### Verification Notes

<!--
  Edit commands below to match this repo's toolchain (npm/pytest/cargo/etc).
  This is the org-wide default; per-repo templates may override.
-->

Each checked box below must be backed by exactly one fenced `evidence` block. The PR-policy parser (warning-only in Phase 1, will hard-fail in Phase 2+) reads them.

Required fields: `command`, `location` (one of `local` / `ci` / `manual`), `result`, `timestamp`. Optional: `check` (used when `location: ci` and the check-run name differs from the command).

TODO: Summarize the exact verification evidence and any manual review.

## Docs / Changelog

TODO: Record the changelog fragment, direct CHANGELOG edit, docs update, or no-changelog label.

## Linked Issue

TODO: Closes #___

## Risks

- Risk level:
- Rollback:
- Follow-ups:
