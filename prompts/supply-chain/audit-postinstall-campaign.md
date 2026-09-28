---
title: "Audit your stack for the postinstall campaign"
slug: "audit-postinstall-campaign"
category: "supply-chain"
type: "prompt"
tags: ["supply-chain", "incident-response"]
source: "https://composedsecurity.com/blog/postinstall-hook-700-repos"
source_label: "Hand to your agent"
---

# Audit your stack for the postinstall campaign

Sweep IOCs, audit lifecycle scripts, disable install scripts, and age out exposed secrets.

> Part of the **Supply Chain & Incident Response** pack. From the Composed Security blog: [700 repos. One postinstall hook.](https://composedsecurity.com/blog/postinstall-hook-700-repos).

## Prompt

```text
Audit my stack for the parikhpreyash4 postinstall campaign.

1. Grep my repo files, lockfiles, and CI workflow YAML for any of:
   parikhpreyash4, /tmp/.sshd, gvfsd-network, curl -skL.

2. Search build logs for the last 30 days for outbound calls to
   github.com/parikhpreyash4/* or any /tmp/.sshd references.

3. Run `npm ls --all --long --json` and surface every dependency
   with a postinstall, preinstall, or prepare lifecycle script.
   For each, cross-check the upstream repo to confirm the commit
   matches what's published.

4. Add --ignore-scripts to my install commands, or set
   ignore-scripts=true in .npmrc. Show me the diff before applying.

5. For every secret in my repo .env files: surface its name and
   age. Anything older than 30 days, recommend rotation. Anything
   touched by a workflow that ran since May 10, rotate immediately.
```

## How to use

Paste the block above into your coding agent (Cursor, Claude Code, Codex, Lovable, or Bolt). Give it read access to the repo. Keep it read-only where the prompt says so, and verify each finding before acting on it.

---

Found this useful? [Composed Security](https://composedsecurity.com) reviews your pull requests for exactly this class of bug.
