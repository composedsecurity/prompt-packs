---
title: "Compromise check for a machine and repo"
slug: "compromise-check-machine-repo"
category: "supply-chain"
type: "prompt"
tags: ["supply-chain", "detection", "incident-response"]
source: "https://composedsecurity.com/blog/github-grafana-popped-supply-chain-playbook"
source_label: "Hand to your agent"
---

# Compromise check for a machine and repo

Eight signals across CI logs, lifecycle scripts, run-time anomalies, audit logs, API usage, keys, and dotfiles.

> Part of the **Supply Chain & Incident Response** pack. From the Composed Security blog: [GitHub got popped. Grafana too. Here's the playbook for everyone else.](https://composedsecurity.com/blog/github-grafana-popped-supply-chain-playbook).

## Prompt

```text
Run a compromise check on this machine and repo. For each signal,
report status (OK / SUSPICIOUS / COMPROMISED) and recommended action.

1. Search GitHub Actions logs in the last 30 days for outbound calls to
   gist.githubusercontent.com, ngrok.io, pipedream.com, or unknown
   raw.githubusercontent.com paths.

2. Search every workflow log in the last 30 days for base64-encoded
   strings over 100 chars. Decode them. Flag anything that decodes
   to credentials or remote payloads.

3. Run `npm ls --all --long --json` and list every dependency with a
   postinstall, preinstall, or install lifecycle script. Cross-check
   the upstream repo to confirm the commit matches what's published.

4. Compare CI run times and log sizes for the last 30 days against
   the prior 90. Flag any 2x or larger jumps.

5. Pull the GitHub org audit log. Flag PAT usage from IPs not seen
   in the prior 90 days. Same for AWS CloudTrail IAM events and
   Stripe Developers activity.

6. Pull the last 30 days of usage from OpenAI, Anthropic, AWS, and
   any other API tied to billing. Flag 2x+ spikes against baseline.

7. List every active deploy key, SSH key, OAuth app, and GitHub App
   on this account with the date added. Flag anything from the last
   30 days I can't immediately explain.

8. Diff `~/.claude/settings.json`, `~/.cursor/`, `~/.vscode/settings.json`,
   `~/.aws/credentials`, `~/.npmrc`, `~/.gitconfig` against their last
   committed or last-known-good versions. Flag any added entries.

Format: one signal per line, status, recommended action.
```

## How to use

Paste the block above into your coding agent (Cursor, Claude Code, Codex, Lovable, or Bolt). Give it read access to the repo. Keep it read-only where the prompt says so, and verify each finding before acting on it.

---

Found this useful? [Composed Security](https://composedsecurity.com) reviews your pull requests for exactly this class of bug.
