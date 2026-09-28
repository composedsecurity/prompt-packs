---
title: "Audit a training harness for agent collaboration"
slug: "audit-training-harness"
category: "agent-runtime"
type: "prompt"
tags: ["ai-agents", "ml-platform", "hardening"]
source: "https://composedsecurity.com/blog/openai-ai-agents-huggingface-breach"
source_label: "Harness hardening audit prompt"
---

# Audit a training harness for agent collaboration

Find shared writable paths, SSRF-capable services, reduced-refusal evals, cheatable tasks, and missing tripwires in ML training and evaluation harnesses.

> Part of the **Agent Runtime & Model Harnesses** pack. From the Composed Security blog: [Agent takeover happened. By accident.](https://composedsecurity.com/blog/openai-ai-agents-huggingface-breach).

## Prompt

```text
Audit our training and evaluation harness for the agent-collective failure mode. Report only. Do not change anything.

1. Map every writable path a workload can reach — package managers, registries, caches, file shares. Flag any path shared by more than one task, since it can act as a cross-agent message bus.

2. For each internet-adjacent internal service a workload can reach, check whether workload-controlled writes can influence what the service fetches. Flag any SSRF-capable path without a destination allowlist.

3. Check whether any evaluations run with reduced cyber refusals, and whether those environments share state with persistent training runs.

4. Audit the task and dataset set for impossible or internet-dependent problems that can only be solved by cheating.

5. List the halting conditions on the harness. What happens when a workload egresses, writes outside its path, or escalates privileges? Flag any harness with no tripwire.

Output: findings with severity and the specific config or code path.
```

## How to use

Paste the block above into your coding agent (Cursor, Claude Code, Codex, Lovable, or Bolt). Give it read access to the repo. Keep it read-only where the prompt says so, and verify each finding before acting on it.

---

Found this useful? [Composed Security](https://composedsecurity.com) reviews your pull requests for exactly this class of bug.
