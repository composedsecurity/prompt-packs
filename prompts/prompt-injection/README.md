# Prompt Injection & Agent Authorization

Stop untrusted text from becoming privileged action.

Prompt injection becomes exploitable when untrusted text can reach an agent that holds real authority. This pack covers the whole loop: audit the agent as an authorization system, detect an active attack, respond to it, and harden the boundary so reading is not the same as acting.

**8 prompts in this pack.** [Back to all packs](../README.md)

## Prompts in this pack

| Prompt | Type | What it does |
|---|---|---|
| [Audit an agentic app as an authorization system](./audit-agentic-authorization.md) | prompt | Inventory every agent tool, find authorization that lives only in a prompt, and trace untrusted input to unauthorized effects. |
| [Audit indirect prompt injection in operational text](./audit-operational-text-injection.md) | prompt | Find agents that ingest Sentry, logs, CI output, issues, tickets, or MCP tool output and can act on it. |
| [Audit a support agent's privileged actions](./audit-privileged-agent-actions.md) | prompt | Find account-altering agent actions authorized by forgeable signals instead of verified identity, and gaps versus the human flow. |
| [Detect a pack-hunt jailbreak session](./detect-pack-hunt-session.md) | prompt | Score a session for Unicode substitution, unclosed document framing, decomposed requests, and anomalous length. |
| [IR runbook for a pack-hunt jailbreak](./ir-pack-hunt-session.md) | prompt | Trace downstream artifacts, assess laundered harmful output, and decide whether disclosure is warranted. |
| [Harden a pipeline against pack hunts](./audit-pack-hunt-hardening.md) | prompt | Audit context persistence, Unicode normalization, secondary classifiers, and server-side authorization. |
| [Harden agents against indirect prompt injection](./harden-indirect-prompt-injection.md) | prompt | Tag input provenance, block untrusted-context execution, sandbox egress, scope secrets, and add an injection test. |
| [Harden a support agent against privileged-action abuse](./harden-privileged-agent-actions.md) | prompt | Move authorization server-side, require verified identity, add approval gates, log and rate-limit, and test forged identities. |

## Recommended order

1. [Audit an agentic app as an authorization system](./audit-agentic-authorization.md)
2. [Audit indirect prompt injection in operational text](./audit-operational-text-injection.md)
3. [Audit a support agent's privileged actions](./audit-privileged-agent-actions.md)
4. [Detect a pack-hunt jailbreak session](./detect-pack-hunt-session.md)
5. [IR runbook for a pack-hunt jailbreak](./ir-pack-hunt-session.md)
6. [Harden a pipeline against pack hunts](./audit-pack-hunt-hardening.md)
7. [Harden agents against indirect prompt injection](./harden-indirect-prompt-injection.md)
8. [Harden a support agent against privileged-action abuse](./harden-privileged-agent-actions.md)

## How to use this pack

If you are building an agent, start with the authorization audit and the operational-text injection audit. If you suspect an active incident, go straight to the detection and IR prompts.

## From the blog

These prompts are explained in full in the posts below. The post is where you get the failure mode, the reasoning, and the edge cases; the prompt is what you run.

- [Muse Rebuilt OpenClaw's Shape. The Prompt Injection Came With It.](https://composedsecurity.com/blog/meta-muse-openclaw-prompt-injection)
- [Anthropic's Safest Model Lasted 24 Hours](https://composedsecurity.com/blog/claude-fable-5-jailbreak)
- [Logs are hostile input now.](https://composedsecurity.com/blog/fake-sentry-alert-prompt-injection)
- [Hackers asked Meta's AI for Instagram accounts. It said yes.](https://composedsecurity.com/blog/meta-ai-instagram-account-takeover)

## Related

- [All prompt packs](../README.md)
- [Secrets & Env Vars](../secrets/README.md)
- [Database](../database/README.md)
- [Authentication & Access Control](../authentication/README.md)
- [API Hardening](../api-hardening/README.md)
- [Release Gate](../release/README.md)
- [Agent Runtime & Model Harnesses](../agent-runtime/README.md)
- [Supply Chain & Incident Response](../supply-chain/README.md)
- [Composed Security blog](https://composedsecurity.com/blog)
