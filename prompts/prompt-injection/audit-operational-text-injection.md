---
title: "Audit indirect prompt injection in operational text"
slug: "audit-operational-text-injection"
category: "prompt-injection"
type: "prompt"
tags: ["prompt-injection", "agentic-security"]
source: "https://composedsecurity.com/blog/fake-sentry-alert-prompt-injection"
source_label: "Hand to your agent"
---

# Audit indirect prompt injection in operational text

Find agents that ingest Sentry, logs, CI output, issues, tickets, or MCP tool output and can act on it.

> Part of the **Prompt Injection & Agent Authorization** pack. From the Composed Security blog: [Logs are hostile input now.](https://composedsecurity.com/blog/fake-sentry-alert-prompt-injection).

## Prompt

```text
Audit how our AI agents handle operational and external text (Sentry, logs, CI output, GitHub issues, Linear webhooks, support tickets, MCP tool output). Report with file paths.

1. List every place an agent ingests text from a source outside our team's direct authorship, and what the agent is allowed to do after reading it.

2. Flag any path where the agent can run a shell command, install a package, or make a network call based on content that came from one of those external sources.

3. Flag any agent that has all three of: access to secrets or private code, exposure to external text, and outbound network access (the lethal trifecta).

4. Check whether agent-proposed commands require human approval before execution, and whether package lifecycle scripts are disabled by default.

Do not change anything. Report only.
```

## How to use

Paste the block above into your coding agent (Cursor, Claude Code, Codex, Lovable, or Bolt). Give it read access to the repo. Keep it read-only where the prompt says so, and verify each finding before acting on it.

---

Found this useful? [Composed Security](https://composedsecurity.com) reviews your pull requests for exactly this class of bug.
