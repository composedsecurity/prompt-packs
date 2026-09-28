# API Hardening

Rate limits, input validation, and payment webhooks.

Every endpoint that trusts its input is blast radius: unbounded spend, injection, or a forged payment event that unlocks paid features for free. This pack hardens the three surfaces that matter most before you expose an API to the public.

**3 prompts in this pack.** [Back to all packs](../README.md)

## Prompts in this pack

| Prompt | Type | What it does |
|---|---|---|
| [Add rate limiting to every API route](./add-rate-limiting.md) | prompt | Classify routes by cost and wire Upstash limiters with correct 429 headers. |
| [Add strict input validation to every endpoint](./add-input-validation.md) | prompt | Zod schemas per endpoint, strict parsing, and a dedicated section for authorization-via-input bugs. |
| [Verify Stripe webhook signatures](./verify-stripe-webhooks.md) | prompt | Raw-body handling, signature verification, idempotency, transactions, and event allowlists. |

## Recommended order

1. [Add rate limiting to every API route](./add-rate-limiting.md)
2. [Add strict input validation to every endpoint](./add-input-validation.md)
3. [Verify Stripe webhook signatures](./verify-stripe-webhooks.md)

## How to use this pack

Add rate limiting and validation to all routes, then verify your webhook signatures. The webhook prompt assumes the others exist; run it last so payment state has one source of truth.

## From the blog

These prompts are explained in full in the posts below. The post is where you get the failure mode, the reasoning, and the edge cases; the prompt is what you run.

- [10 Copy-Paste Security Prompts for Your AI Agent](https://composedsecurity.com/blog/10-security-prompts-for-vibe-coders)

## Related

- [All prompt packs](../README.md)
- [Secrets & Env Vars](../secrets/README.md)
- [Database](../database/README.md)
- [Authentication & Access Control](../authentication/README.md)
- [Release Gate](../release/README.md)
- [Prompt Injection & Agent Authorization](../prompt-injection/README.md)
- [Agent Runtime & Model Harnesses](../agent-runtime/README.md)
- [Supply Chain & Incident Response](../supply-chain/README.md)
- [Composed Security blog](https://composedsecurity.com/blog)
