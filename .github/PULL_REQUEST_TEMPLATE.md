<!--
  This template is the default for any repo under @ArchonVII that does not
  ship its own PULL_REQUEST_TEMPLATE.md.

  If your repo opts into the shared `pr-policy` reusable workflow from
  ArchonVII/github-workflows, non-draft PRs must satisfy ALL of:

    1. `## Verification`          (H2, exact text)
    2. `### Verification Notes`   (H3, exact text, nested under 1)
    3. At least one CHECKED box   (`- [x]` somewhere in the body)
    4. Linked issue               (`Closes #N`, `Fixes #N`, or `Refs #N`)

  Doc-only PRs (every changed file is `.md`/`.txt`/an image/`.changelog/**`)
  skip the verification ceremony.

  Tick a verification box `[x]` only after the command actually passed.
-->

## Summary

<!-- What changed and why? -->

## Linked Issue

Closes #

## Scope

- In scope:
- Out of scope:

## Changelog

<!-- Fragment: .changelog/unreleased/<issue>-<slug>.md, CHANGELOG.md direct edit, no-changelog label, or N/A with reason. -->

## Verification

### Verification Notes

<!--
  Edit commands below to match this repo's toolchain (npm/pytest/cargo/etc).
  This is the org-wide default; per-repo templates may override.
-->

Each checked box below must be backed by exactly one fenced `evidence` block. The PR-policy parser (warning-only in Phase 1, will hard-fail in Phase 2+) reads them.

Required fields: `command`, `location` (one of `local` / `ci` / `manual`), `result`, `timestamp`. Optional: `check` (used when `location: ci` and the check-run name differs from the command).

- [ ] Tests pass

  ```evidence
  command: npm test
  location: local
  result: 16/16 passing
  timestamp: 2026-05-20T18:32:00Z
  ```

- [ ] CI green on this branch

  ```evidence
  command: vitest
  location: ci
  result: success
  timestamp: 2026-05-20T18:39:00Z
  ```

- [ ] Visual / manual review

  ```evidence
  command: read full diff in GitHub UI
  location: manual
  result: no concerns
  timestamp: 2026-05-20T18:41:00Z
  ```

## Risks

- Risk level:
- Rollback:
- Follow-ups:
