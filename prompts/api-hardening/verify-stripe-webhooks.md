---
title: "Verify Stripe webhook signatures"
slug: "verify-stripe-webhooks"
category: "api-hardening"
type: "prompt"
tags: ["stripe", "webhooks", "payments"]
source: "https://composedsecurity.com/blog/10-security-prompts-for-vibe-coders"
source_label: "Prompt 8"
---

# Verify Stripe webhook signatures

Raw-body handling, signature verification, idempotency, transactions, and event allowlists.

> Part of the **API Hardening** pack. From the Composed Security blog: [10 Copy-Paste Security Prompts for Your AI Agent](https://composedsecurity.com/blog/10-security-prompts-for-vibe-coders).

## Prompt

```text
Secure Stripe webhook integration. Other webhook handlers (Slack, GitHub, custom) get the same treatment.

Step 1: find every webhook receiver. Stripe POST routes (api/webhooks/stripe, api/stripe/webhook). Other webhooks (Slack signing, GitHub HMAC, Twilio): list each + current verification status. Output: Service, Endpoint, Verifies signature?

Step 2: fix Stripe endpoint in this order. (a) Raw body. Stripe verification needs exact raw bytes. Next.js App Router: `await request.text()`, NOT `request.json()`. Next.js Pages Router: `export const config = { api: { bodyParser: false } }`; read with stream. Express: `express.raw({ type: 'application/json' })` only on webhook route. Show framework-specific fix as diff.

(b) Signature verification. `stripe.webhooks.constructEvent(rawBody, signatureHeader, STRIPE_WEBHOOK_SECRET)`. try/catch. Failure = 400 immediately. Do NOT process. `STRIPE_WEBHOOK_SECRET` from env (never hardcode); add to `.env.example`. Signature from header `stripe-signature`.

(c) Idempotency. Stripe retries non-2xx for 3 days. Don't double-process. Add `event_id` table (or use existing). INSERT...ON CONFLICT DO NOTHING with event.id as PK BEFORE processing. 0 rows affected = already processed. Return 200. Show migration (SQL/Prisma/Drizzle).

(d) Processing. Wrap in DB transaction. Return 200 only after commit. Unexpected error during processing: 500 (Stripe retries). Log event_id.

(e) Event type whitelist. Handle expected types only (checkout.session.completed, invoice.paid). Unhandled types: 200, no action. Don't error.

Step 3: env var checklist. `STRIPE_SECRET_KEY` (server-only). `STRIPE_WEBHOOK_SECRET` (per endpoint, separate from API key). `NEXT_PUBLIC_STRIPE_PUBLISHABLE_KEY` (client-safe; pk_live_/pk_test_). Webhook secret location: Stripe dashboard, Developers, Webhooks, click endpoint, Reveal signing secret.

Step 4: test. `stripe listen --forward-to localhost:3000/api/webhooks/stripe`. `stripe trigger checkout.session.completed`. Assert: signature verification works, replay rejected, unexpected event types return 200 no-op.

Step 5: FLAG any code reading payment status / subscription status / "isPaid" from CLIENT or request body. CRITICAL. Source of truth is database state set BY verified webhook. Never trust client to declare payment. For non-Stripe webhooks from step 1: same pattern (raw body, signature header, env var, idempotency).
```

## How to use

Paste the block above into your coding agent (Cursor, Claude Code, Codex, Lovable, or Bolt). Give it read access to the repo. Keep it read-only where the prompt says so, and verify each finding before acting on it.

---

Found this useful? [Composed Security](https://composedsecurity.com) reviews your pull requests for exactly this class of bug.
