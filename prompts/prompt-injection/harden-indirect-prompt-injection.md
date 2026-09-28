---
title: "Harden agents against indirect prompt injection"
slug: "harden-indirect-prompt-injection"
category: "prompt-injection"
type: "prompt"
tags: ["prompt-injection", "hardening"]
source: "https://composedsecurity.com/blog/fake-sentry-alert-prompt-injection"
source_label: "The fix, in one brief"
---

# Harden agents against indirect prompt injection

Tag input provenance, block untrusted-context execution, sandbox egress, scope secrets, and add an injection test.

> Part of the **Prompt Injection & Agent Authorization** pack. From the Composed Security blog: [Logs are hostile input now.](https://composedsecurity.com/blog/fake-sentry-alert-prompt-injection).

## Prompt

```text
Harden our agents against indirect prompt injection from operational text. Implement, then show diffs.

1. Tag every input by provenance (user, trusted internal, external or untrusted) and pass that tag into the agent context.

2. Block the agent from executing shell commands, package installs, or network calls that originate from external or untrusted content. Require explicit human approval for those actions.

3. Default the agent runtime to no outbound network except an allowlist. Remove standing secrets from its environment and inject only what a task needs, scoped and short-lived.

4. Set ignore-scripts=true for npm in agent and CI environments, and pin dependencies.

5. Add a test: feed the agent a fake alert that says run this command, and assert it refuses and flags it.
```

## How to use

Paste the block above into your coding agent (Cursor, Claude Code, Codex, Lovable, or Bolt). Give it read access to the repo. Keep it read-only where the prompt says so, and verify each finding before acting on it.

---

Found this useful? [Composed Security](https://composedsecurity.com) reviews your pull requests for exactly this class of bug.
