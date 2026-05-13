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

## Verification

- [ ] Lint passes
- [ ] Tests pass
- [ ] Manual verification documented below when applicable

### Verification Notes

<!-- Record exact commands/results, screenshots, or manual smoke-test notes. -->

## Risks

- Risk level:
- Rollback:
- Follow-ups:
