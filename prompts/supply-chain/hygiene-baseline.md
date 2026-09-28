---
title: "Set a supply-chain hygiene baseline"
slug: "hygiene-baseline"
category: "supply-chain"
type: "prompt"
tags: ["supply-chain", "hardening"]
source: "https://composedsecurity.com/blog/github-grafana-popped-supply-chain-playbook"
source_label: "Hand to your agent"
---

# Set a supply-chain hygiene baseline

Lockfiles, SHA-pinned Actions, extension audit, gitleaks, and a weekly audit-log review.

> Part of the **Supply Chain & Incident Response** pack. From the Composed Security blog: [GitHub got popped. Grafana too. Here's the playbook for everyone else.](https://composedsecurity.com/blog/github-grafana-popped-supply-chain-playbook).

## Prompt

```text
Set up hygiene baseline on this repo and machine.

1. Lockfile state: Confirm a lockfile is committed. Switch CI to
   `npm ci` / `pnpm install --frozen-lockfile` / `yarn install --immutable`.
   Show me the diff.

2. GitHub Actions pinning: Walk every .github/workflows/*.yml. For
   each third-party `uses:` line, look up the full 40-char SHA for
   the current tag and rewrite as `uses: owner/action@<sha>  # vX.Y.Z`.
   Generate a Renovate config with pinDigests.

3. Extension audit: List every VS Code and Cursor extension currently
   installed. For each: publisher, install count, last update, current
   version. Flag any with unverified publisher, fewer than 1000
   installs, or updated within the last 7 days.

4. Secret scanning: Run `gitleaks detect --source . --log-opts="--all"
   --report-format json`. For each finding: file, line, commit, secret
   type, rotation procedure. Then turn on GitHub Secret Scanning Push
   Protection.

5. Weekly recurring task: Pull the GitHub org audit log diff for the
   last 7 days. Surface any new tokens, deploy keys, OAuth grants, or
   workflow changes I didn't author.

Show me what you've changed before applying anything.
```

## How to use

Paste the block above into your coding agent (Cursor, Claude Code, Codex, Lovable, or Bolt). Give it read access to the repo. Keep it read-only where the prompt says so, and verify each finding before acting on it.

---

Found this useful? [Composed Security](https://composedsecurity.com) reviews your pull requests for exactly this class of bug.
