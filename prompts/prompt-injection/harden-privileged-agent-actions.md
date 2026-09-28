---
title: "Harden a support agent against privileged-action abuse"
slug: "harden-privileged-agent-actions"
category: "prompt-injection"
type: "prompt"
tags: ["ai-agents", "authorization", "hardening"]
source: "https://composedsecurity.com/blog/meta-ai-instagram-account-takeover"
source_label: "The fix, in one brief"
---

# Harden a support agent against privileged-action abuse

Move authorization server-side, require verified identity, add approval gates, log and rate-limit, and test forged identities.

> Part of the **Prompt Injection & Agent Authorization** pack. From the Composed Security blog: [Hackers asked Meta's AI for Instagram accounts. It said yes.](https://composedsecurity.com/blog/meta-ai-instagram-account-takeover).

## Prompt

```text
Harden our AI agent against privileged-action abuse. Implement, then show me the diffs.

1. Move every account-altering action behind a server-side authorization check the model cannot bypass. The model may request the action; the data layer authorizes it.

2. Require verified identity (proven control of the existing email or phone, a passkey, or MFA) before email change, password or MFA reset, payouts, and role changes. Remove any reliance on IP or geolocation as proof.

3. Add a human-in-the-loop approval gate for irreversible actions, plus a user-facing path to reach a human to reverse one.

4. Log every privileged agent action with actor, target, and authorizing check, and rate-limit them per account and per session.

5. Write tests that attempt each privileged action with a forged location and a self-asserted identity, and assert they are denied.
```

## How to use

Paste the block above into your coding agent (Cursor, Claude Code, Codex, Lovable, or Bolt). Give it read access to the repo. Keep it read-only where the prompt says so, and verify each finding before acting on it.

---

Found this useful? [Composed Security](https://composedsecurity.com) reviews your pull requests for exactly this class of bug.
