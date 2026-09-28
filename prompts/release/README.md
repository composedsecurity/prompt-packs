# Release Gate

The pre-deployment go/no-go check.

One pass over the whole app before you ship it. The release gate runs twenty-seven checks across secrets, database, auth, API, payments, access control, infrastructure, and code hygiene, and refuses to say GO if any CRITICAL item fails.

**1 prompt in this pack.** [Back to all packs](../README.md)

## Prompts in this pack

| Prompt | Type | What it does |
|---|---|---|
| [Pre-deployment security go/no-go check](./pre-deploy-security-check.md) | prompt | Twenty-seven checks across secrets, database, auth, API, payments, access control, infrastructure, and hygiene. |

## How to use this pack

Run this last, after the other packs. It is a read-only audit that produces a table with a verdict. Treat one CRITICAL fail as a hard stop.

## From the blog

These prompts are explained in full in the posts below. The post is where you get the failure mode, the reasoning, and the edge cases; the prompt is what you run.

- [10 Copy-Paste Security Prompts for Your AI Agent](https://composedsecurity.com/blog/10-security-prompts-for-vibe-coders)

## Related

- [All prompt packs](../README.md)
- [Secrets & Env Vars](../secrets/README.md)
- [Database](../database/README.md)
- [Authentication & Access Control](../authentication/README.md)
- [API Hardening](../api-hardening/README.md)
- [Prompt Injection & Agent Authorization](../prompt-injection/README.md)
- [Agent Runtime & Model Harnesses](../agent-runtime/README.md)
- [Supply Chain & Incident Response](../supply-chain/README.md)
- [Composed Security blog](https://composedsecurity.com/blog)
