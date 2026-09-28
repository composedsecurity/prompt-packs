---
title: "Add rate limiting to every API route"
slug: "add-rate-limiting"
category: "api-hardening"
type: "prompt"
tags: ["api", "rate-limiting"]
source: "https://composedsecurity.com/blog/10-security-prompts-for-vibe-coders"
source_label: "Prompt 5"
---

# Add rate limiting to every API route

Classify routes by cost and wire Upstash limiters with correct 429 headers.

> Part of the **API Hardening** pack. From the Composed Security blog: [10 Copy-Paste Security Prompts for Your AI Agent](https://composedsecurity.com/blog/10-security-prompts-for-vibe-coders).

## Prompt

```text
Add rate limiting to every API route. Use Upstash Ratelimit + Upstash Redis (free tier covers most apps) unless I say otherwise.

Step 1: detect framework + routes. Next.js App Router: `app/**/route.{ts,js}`. Next.js Pages: `pages/api/**/*`. Express/Fastify/Hono: route registrations. Server Actions: `app/**` with "use server". Output: every route with path, method, file.

Step 2: classify. HIGH_COST: paid LLM API (OpenAI, Anthropic, Replicate, ElevenLabs); emails/SMS; expensive third-party. MEDIUM_COST: DB writes, file uploads, complex queries. LOW_COST: simple reads, public endpoints, health checks. AUTH_SENSITIVE: login, signup, password reset (limit by IP, NOT user). Default limits: HIGH_COST 10/min/user + 30/min/IP. MEDIUM_COST 60/min/user. LOW_COST 300/min/IP. AUTH_SENSITIVE 5/min/IP + 10/hour/IP. Override if I say.

Step 3: implementation. Install `@upstash/ratelimit @upstash/redis`. Shared limiter file (`lib/ratelimit.ts`) with one limiter per cost class, sliding-window strategy. Insert limiter at top of each handler, before any expensive work. Identifier: user ID from session if available, else IP from `x-forwarded-for` (fallback: direct IP). On limit: 429 with headers `Retry-After`, `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset`. Body: `{"error":"rate_limit_exceeded","retryAfter":<seconds>}`.

Step 4: env vars. `UPSTASH_REDIS_REST_URL`, `UPSTASH_REDIS_REST_TOKEN`. Add to `.env.local` + `.env.example`. Note in deployment checklist.

Step 5: observability. Log every 429 with route, identifier, limit class. If Sentry/Logtail/Axiom present, route logs there.

Step 6: test plan. Per cost class, one curl one-liner that exercises the limit.

Do NOT change route logic beyond inserting the rate-limit check. Cost class unclear? Ask before classifying.
```

## How to use

Paste the block above into your coding agent (Cursor, Claude Code, Codex, Lovable, or Bolt). Give it read access to the repo. Keep it read-only where the prompt says so, and verify each finding before acting on it.

---

Found this useful? [Composed Security](https://composedsecurity.com) reviews your pull requests for exactly this class of bug.
