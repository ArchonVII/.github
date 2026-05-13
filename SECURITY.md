# Security Policy

This is the default security policy for repos under [@ArchonVII](https://github.com/ArchonVII) that do not ship their own `SECURITY.md`.

## Reporting a Vulnerability

**Do not open a public issue for security vulnerabilities.**

Instead, report privately one of these ways:

1. **GitHub private vulnerability reporting** — preferred. On the affected repo, go to the **Security** tab and click **Report a vulnerability**. This creates a private advisory only visible to maintainers.
2. **Email** — `josephmaguirre@gmail.com` with `[SECURITY]` in the subject. Include:
   - Affected repo and version / commit
   - Reproduction steps
   - Impact assessment
   - Any suggested mitigation

## What to expect

- I will acknowledge receipt within 7 days.
- I will give a triage assessment (accepted / not-a-vuln / needs-info) within 14 days.
- Fixes for accepted reports land in a private branch first, then a coordinated public disclosure once a patch is available.

## Scope

These repos are personal / hobby projects without a paid security program. There is no bug bounty. I appreciate responsible disclosure all the same.

## Supported Versions

For repos that don't tag releases, only the latest `main` is supported. For repos with tagged releases, the latest minor of the latest major is supported.
