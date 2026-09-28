---
title: "Harden a pipeline against pack hunts"
slug: "audit-pack-hunt-hardening"
category: "prompt-injection"
type: "prompt"
tags: ["jailbreak", "hardening"]
source: "https://composedsecurity.com/blog/claude-fable-5-jailbreak"
source_label: "Hardening audit prompt"
---

# Harden a pipeline against pack hunts

Audit context persistence, Unicode normalization, secondary classifiers, and server-side authorization.

> Part of the **Prompt Injection & Agent Authorization** pack. From the Composed Security blog: [Anthropic's Safest Model Lasted 24 Hours](https://composedsecurity.com/blog/claude-fable-5-jailbreak).

## Prompt

```text
Audit our agentic pipeline for pack hunt vulnerability. Check: (1) Do any agent sessions persist context across more than 20 turns without a forced reset? (2) Is user input passed to the model before Unicode normalization? (3) Do we have a separate classifier (ideally on a different provider) that checks for document-type framing before passing user input to a privileged agent? (4) Are any privileged actions (database writes, API calls, code execution) enforced at the model layer only, with no server-side authorization check? Return a finding for each gap with a severity rating and a one-line remediation.
```

## How to use

Paste the block above into your coding agent (Cursor, Claude Code, Codex, Lovable, or Bolt). Give it read access to the repo. Keep it read-only where the prompt says so, and verify each finding before acting on it.

---

Found this useful? [Composed Security](https://composedsecurity.com) reviews your pull requests for exactly this class of bug.
