# Authentication & Access Control

Audit logins and move authorization server-side.

Auth bugs are the fastest route to account takeover. These two prompts attack it from both sides: one audits the login and session flow, the other finds authorization checks that only exist in the browser, where anyone can flip them with DevTools.

**2 prompts in this pack.** [Back to all packs](../README.md)

## Prompts in this pack

| Prompt | Type | What it does |
|---|---|---|
| [Audit an authentication flow](./audit-auth-flow.md) | prompt | A CRITICAL/HIGH/MEDIUM review of token storage, session verification, OAuth state, and rate limits. |
| [Find frontend-only access controls](./audit-frontend-only-authz.md) | prompt | Locate client-side authorization checks and generate the backend or RLS enforcement to back them. |

## Recommended order

1. [Audit an authentication flow](./audit-auth-flow.md)
2. [Find frontend-only access controls](./audit-frontend-only-authz.md)

## How to use this pack

Run the auth flow audit first to map your stack, then the frontend-only access-control audit to find the checks that have no backend equivalent. Keep the frontend checks; just make sure the backend enforces every one.

## From the blog

These prompts are explained in full in the posts below. The post is where you get the failure mode, the reasoning, and the edge cases; the prompt is what you run.

- [10 Copy-Paste Security Prompts for Your AI Agent](https://composedsecurity.com/blog/10-security-prompts-for-vibe-coders)

## Related

- [All prompt packs](../README.md)
- [Secrets & Env Vars](../secrets/README.md)
- [Database](../database/README.md)
- [API Hardening](../api-hardening/README.md)
- [Release Gate](../release/README.md)
- [Prompt Injection & Agent Authorization](../prompt-injection/README.md)
- [Agent Runtime & Model Harnesses](../agent-runtime/README.md)
- [Supply Chain & Incident Response](../supply-chain/README.md)
- [Composed Security blog](https://composedsecurity.com/blog)
