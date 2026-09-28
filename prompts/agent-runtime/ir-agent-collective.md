---
title: "Incident response runbook for agent collectives"
slug: "ir-agent-collective"
category: "agent-runtime"
type: "prompt"
tags: ["ai-agents", "incident-response"]
source: "https://composedsecurity.com/blog/openai-ai-agents-huggingface-breach"
source_label: "Defensive agent IR runbook"
---

# Incident response runbook for agent collectives

Pull 30 days of logs, hunt the six signals, trace exposed credentials, build a timeline, and add real-time detections.

> Part of the **Agent Runtime & Model Harnesses** pack. From the Composed Security blog: [Agent takeover happened. By accident.](https://composedsecurity.com/blog/openai-ai-agents-huggingface-breach).

## Prompt

```text
Treat this as a live incident runbook. We suspect an agent-collective incident involving our [ENVIRONMENT] workloads. Do not change anything. Report only.

1. Pull logs across package registries, artifact stores, and training or evaluation environments for the last 30 days and export to a file.

2. Hunt for the six signals from the IOC checklist: ghost writes to registries, outbound fetches by internal services, legacy auth successes, kernel-exploit behavior, IMDS or broad Kubernetes API access, and sustained egress to third-party hosts. Produce one finding per signal with the log line and severity.

3. For every credential found on the affected paths, trace where it was used inside and outside our perimeter. Flag any that were used at third-party organizations and list the organizations to coordinate revocation with.

4. Build a timeline of the activity and recommend containment actions, ordered by risk.

5. Propose automated detections for each signal so this pattern alerts in real time next time.
```

## How to use

Paste the block above into your coding agent (Cursor, Claude Code, Codex, Lovable, or Bolt). Give it read access to the repo. Keep it read-only where the prompt says so, and verify each finding before acting on it.

---

Found this useful? [Composed Security](https://composedsecurity.com) reviews your pull requests for exactly this class of bug.
