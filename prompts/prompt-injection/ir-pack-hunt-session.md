---
title: "IR runbook for a pack-hunt jailbreak"
slug: "ir-pack-hunt-session"
category: "prompt-injection"
type: "prompt"
tags: ["jailbreak", "incident-response"]
source: "https://composedsecurity.com/blog/claude-fable-5-jailbreak"
source_label: "IR runbook prompt"
---

# IR runbook for a pack-hunt jailbreak

Trace downstream artifacts, assess laundered harmful output, and decide whether disclosure is warranted.

> Part of the **Prompt Injection & Agent Authorization** pack. From the Composed Security blog: [Anthropic's Safest Model Lasted 24 Hours](https://composedsecurity.com/blog/claude-fable-5-jailbreak).

## Prompt

```text
A session in our LLM pipeline was flagged for potential multi-agent jailbreak priming (pack hunt pattern). The session ID is [SESSION_ID]. Steps: (1) Pull the full session transcript from our logging system and export to a file. (2) Scan the transcript for Unicode homoglyph substitution in user messages. (3) Identify any explicit document-type framing (research paper, CTF prep, fiction, exam) that was established and not closed. (4) List all downstream artifacts (code files, config changes, instructions, API calls) generated from this session. (5) For each downstream artifact, assess whether the content could constitute harmful output that was laundered through the framing attack. (6) Produce a risk summary: affected artifacts, recommended remediation, and whether incident disclosure is warranted.
```

## How to use

Paste the block above into your coding agent (Cursor, Claude Code, Codex, Lovable, or Bolt). Give it read access to the repo. Keep it read-only where the prompt says so, and verify each finding before acting on it.

---

Found this useful? [Composed Security](https://composedsecurity.com) reviews your pull requests for exactly this class of bug.
