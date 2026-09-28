---
title: "Audit a support agent's privileged actions"
slug: "audit-privileged-agent-actions"
category: "prompt-injection"
type: "prompt"
tags: ["ai-agents", "authorization", "account-takeover"]
source: "https://composedsecurity.com/blog/meta-ai-instagram-account-takeover"
source_label: "Hand to your agent"
---

# Audit a support agent's privileged actions

Find account-altering agent actions authorized by forgeable signals instead of verified identity, and gaps versus the human flow.

> Part of the **Prompt Injection & Agent Authorization** pack. From the Composed Security blog: [Hackers asked Meta's AI for Instagram accounts. It said yes.](https://composedsecurity.com/blog/meta-ai-instagram-account-takeover).

## Prompt

```text
Audit this codebase for the Meta-AI-support-bot failure mode: an AI agent with privileged actions and weak authorization.

1. List every action our AI agent, chatbot, or support assistant can trigger that changes account state: email or phone changes, password or MFA resets, refunds or payouts, role or permission grants, data export, deletion.

2. For each, show what authorizes the action. Flag anything that relies on a forgeable signal (IP or geolocation, a self-asserted identifier, an unverified email) instead of a verified identity or session.

3. Compare the agent path to our standard human or UI flow for the same action. Flag any action where the agent path requires less proof.

4. Flag any state-changing or irreversible action the agent can take with no human-in-the-loop approval.

5. Confirm every privileged agent action is logged and rate-limited.

Report each finding with file path, the authorizing check, and the gap. Do not change code. Report only.
```

## How to use

Paste the block above into your coding agent (Cursor, Claude Code, Codex, Lovable, or Bolt). Give it read access to the repo. Keep it read-only where the prompt says so, and verify each finding before acting on it.

---

Found this useful? [Composed Security](https://composedsecurity.com) reviews your pull requests for exactly this class of bug.
