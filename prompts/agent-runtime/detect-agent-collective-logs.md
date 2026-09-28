---
title: "Detect agent-collective activity in your logs"
slug: "detect-agent-collective-logs"
category: "agent-runtime"
type: "prompt"
tags: ["ai-agents", "detection", "logging"]
source: "https://composedsecurity.com/blog/openai-ai-agents-huggingface-breach"
source_label: "Detection agent prompt"
---

# Detect agent-collective activity in your logs

Six log signals for autonomous agents teaming up: ghost registry writes, SSRF fetches, legacy auth abuse, kernel exploits, IMDS access, and training-env egress.

> Part of the **Agent Runtime & Model Harnesses** pack. From the Composed Security blog: [Agent takeover happened. By accident.](https://composedsecurity.com/blog/openai-ai-agents-huggingface-breach).

## Prompt

```text
Scan our logs for signs of the agent-collective pattern. Do not change anything. Report findings only, with evidence and a severity for each.

1. Find writes or directory creations in our package registries and artifact stores that did not come from a build pipeline. Flag names that look like agent handles, base64 blobs, or 'ZZ'-prefixed artifacts.

2. Find internal services (package managers, caches, proxies) making outbound fetches to arbitrary external URLs not on our allowlist, especially fetch-then-write or fetch-then-exfil sequences.

3. Find auth events on legacy or decommissioned endpoints, and any token issuance where an invalid-signature flow returned success.

4. Find container workloads performing kernel exploit primitives, namespace escapes, or unusual /proc or /sys access.

5. Find workload identities accessing IMDS or metadata endpoints, or making Kubernetes API calls beyond their defined role.

6. Find sustained outbound traffic from training or evaluation environments to external third-party hosts.

Output: one finding per signal with the log line, the severity, and the alert that should have fired.
```

## How to use

Paste the block above into your coding agent (Cursor, Claude Code, Codex, Lovable, or Bolt). Give it read access to the repo. Keep it read-only where the prompt says so, and verify each finding before acting on it.

---

Found this useful? [Composed Security](https://composedsecurity.com) reviews your pull requests for exactly this class of bug.
