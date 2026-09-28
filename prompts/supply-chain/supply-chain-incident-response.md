---
title: "Supply-chain incident response playbook"
slug: "supply-chain-incident-response"
category: "supply-chain"
type: "prompt"
tags: ["supply-chain", "incident-response"]
source: "https://composedsecurity.com/blog/github-grafana-popped-supply-chain-playbook"
source_label: "Hand to your agent"
---

# Supply-chain incident response playbook

Six phases: contain, scope, audit logs, rotate, hunt persistence, notify.

> Part of the **Supply Chain & Incident Response** pack. From the Composed Security blog: [GitHub got popped. Grafana too. Here's the playbook for everyone else.](https://composedsecurity.com/blog/github-grafana-popped-supply-chain-playbook).

## Prompt

```text
I think I've been compromised. Walk me through incident response.

Phase 1 - Contain (next 30 minutes):
- List every CI workflow currently enabled. Help me disable.
- List every active token (npm, GitHub PAT, deploy keys, AWS keys,
  Stripe keys, every SaaS in my config). For each that had any path
  to production, REVOKE (not rotate) immediately.

Phase 2 - Scope:
- For the suspected compromised path, list every token in scope.
- For each token, list what it had access to (cloud roles, repo
  scopes, registry scopes).
- Tell me the worst-case data exposure given that scope.

Phase 3 - Log audit:
- Pull and summarize the GitHub org audit log, AWS CloudTrail, npm
  publish history, and every other SaaS audit log I can authenticate
  to. Last 90 days.
- Flag every event involving a token in the compromised scope.

Phase 4 - Rotate:
- Generate a rotation checklist for every token, key, secret, and
  OAuth grant in the blast radius. Group by provider. Cross-reference
  against audit findings so we don't miss one.

Phase 5 - Persistence hunt:
- List every deploy key, IAM user, GitHub App, OAuth app, scheduled
  workflow, and cron job created in the affected window. Flag
  anything I can't explain.

Phase 6 - Notify and document:
- Draft notification emails to my team, affected users, and providers
  based on the actual scope.
- Draft a public postmortem with timeline, root cause, scope, and
  what we changed. Use Grafana, Vercel, and GitHub May 2026 incident
  reports as style references.
```

## How to use

Paste the block above into your coding agent (Cursor, Claude Code, Codex, Lovable, or Bolt). Give it read access to the repo. Keep it read-only where the prompt says so, and verify each finding before acting on it.

---

Found this useful? [Composed Security](https://composedsecurity.com) reviews your pull requests for exactly this class of bug.
