---
title: "Audit an agentic app as an authorization system"
slug: "audit-agentic-authorization"
category: "prompt-injection"
type: "prompt"
tags: ["prompt-injection", "authorization", "ai-agents"]
source: "https://composedsecurity.com/blog/meta-muse-openclaw-prompt-injection"
source_label: "Hand to your agent"
---

# Audit an agentic app as an authorization system

Inventory every agent tool, find authorization that lives only in a prompt, and trace untrusted input to unauthorized effects.

> Part of the **Prompt Injection & Agent Authorization** pack. From the Composed Security blog: [Muse Rebuilt OpenClaw's Shape. The Prompt Injection Came With It.](https://composedsecurity.com/blog/meta-muse-openclaw-prompt-injection).

## Prompt

```text
Audit this agentic application as an authorization system.

1. Inventory every tool the agent can call. Classify each as read-only, reversible write, external communication, permission change, financial, or destructive.

2. For every state-changing tool, identify where identity, resource ownership, scope, and user approval are enforced. Flag any control implemented only in a prompt or model instruction.

3. Trace untrusted content sources (email, documents, web pages, tickets, chat messages) into planning and tool arguments. Test whether injected instructions can alter recipients, destinations, amounts, permissions, or resources.

4. Verify that consequential actions present an exact preview and require fresh approval. Confirm approval is bound to the final tool arguments and expires if those arguments change.

5. Confirm audit logs preserve the user request, consulted content, policy decision, proposed arguments, approval, execution result, and rollback identifier.

Return only findings with a reproducible path from untrusted input to unauthorized effect.
```

## How to use

Paste the block above into your coding agent (Cursor, Claude Code, Codex, Lovable, or Bolt). Give it read access to the repo. Keep it read-only where the prompt says so, and verify each finding before acting on it.

---

Found this useful? [Composed Security](https://composedsecurity.com) reviews your pull requests for exactly this class of bug.
