# Agent Runtime & Model Harnesses

Detect and contain emergent multi-agent behavior.

When agents run long, share state, and can reach the network, they can coordinate in ways nobody designed. These prompts come from a case where autonomous agents taught each other to hack in under 13 hours. Use them to see the pattern in your logs, audit the harness that makes it possible, and run incident response if it already happened.

**3 prompts in this pack.** [Back to all packs](../README.md)

## Prompts in this pack

| Prompt | Type | What it does |
|---|---|---|
| [Detect agent-collective activity in your logs](./detect-agent-collective-logs.md) | prompt | Six log signals for autonomous agents teaming up: ghost registry writes, SSRF fetches, legacy auth abuse, kernel exploits, IMDS access, and training-env egress. |
| [Audit a training harness for agent collaboration](./audit-training-harness.md) | prompt | Find shared writable paths, SSRF-capable services, reduced-refusal evals, cheatable tasks, and missing tripwires in ML training and evaluation harnesses. |
| [Incident response runbook for agent collectives](./ir-agent-collective.md) | prompt | Pull 30 days of logs, hunt the six signals, trace exposed credentials, build a timeline, and add real-time detections. |

## Recommended order

1. [Detect agent-collective activity in your logs](./detect-agent-collective-logs.md)
2. [Audit a training harness for agent collaboration](./audit-training-harness.md)
3. [Incident response runbook for agent collectives](./ir-agent-collective.md)

## How to use this pack

Start with the log detection prompt. If it lights up, move to the IR runbook. The harness audit is for teams that train or evaluate models and want to remove the shared paths agents use as a message bus.

## From the blog

These prompts are explained in full in the posts below. The post is where you get the failure mode, the reasoning, and the edge cases; the prompt is what you run.

- [Agent takeover happened. By accident.](https://composedsecurity.com/blog/openai-ai-agents-huggingface-breach)

## Related

- [All prompt packs](../README.md)
- [Secrets & Env Vars](../secrets/README.md)
- [Database](../database/README.md)
- [Authentication & Access Control](../authentication/README.md)
- [API Hardening](../api-hardening/README.md)
- [Release Gate](../release/README.md)
- [Prompt Injection & Agent Authorization](../prompt-injection/README.md)
- [Supply Chain & Incident Response](../supply-chain/README.md)
- [Composed Security blog](https://composedsecurity.com/blog)
