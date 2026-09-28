# Secrets & Env Vars

Find, move, and permanently scrub credentials.

Credentials fail in three stages: they sit in code, they get committed, and they survive in history forever. This pack walks all three in order. Run the audit first so you know what you are dealing with, move what is still active into env vars, then scrub anything that already reached git.

**3 prompts in this pack.** [Back to all packs](../README.md)

## Prompts in this pack

| Prompt | Type | What it does |
|---|---|---|
| [Find every exposed secret in a repo](./audit-exposed-secrets.md) | prompt | A read-only secret audit with provider regexes, redacted output, severity, and a rotation action per finding. |
| [Move hardcoded secrets into environment variables](./migrate-secrets-to-env.md) | prompt | Detect the framework, classify server versus client values, and produce a deployment checklist. |
| [Scrub a leaked secret from git history](./scrub-secrets-from-git-history.md) | prompt | A git-filter-repo playbook: revoke first, scrub, verify, force-push, and hunt the copies. |

## Recommended order

1. [Find every exposed secret in a repo](./audit-exposed-secrets.md)
2. [Move hardcoded secrets into environment variables](./migrate-secrets-to-env.md)
3. [Scrub a leaked secret from git history](./scrub-secrets-from-git-history.md)

## How to use this pack

Start with the exposed-secret audit. It is read-only and produces the inventory the other two prompts depend on. Do not scrub history before rotating the leaked credential with the provider, and do not delete hardcoded values until the new env vars work locally.

## From the blog

These prompts are explained in full in the posts below. The post is where you get the failure mode, the reasoning, and the edge cases; the prompt is what you run.

- [10 Copy-Paste Security Prompts for Your AI Agent](https://composedsecurity.com/blog/10-security-prompts-for-vibe-coders)

## Related

- [All prompt packs](../README.md)
- [Database](../database/README.md)
- [Authentication & Access Control](../authentication/README.md)
- [API Hardening](../api-hardening/README.md)
- [Release Gate](../release/README.md)
- [Prompt Injection & Agent Authorization](../prompt-injection/README.md)
- [Agent Runtime & Model Harnesses](../agent-runtime/README.md)
- [Supply Chain & Incident Response](../supply-chain/README.md)
- [Composed Security blog](https://composedsecurity.com/blog)
