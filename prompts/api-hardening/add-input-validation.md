---
title: "Add strict input validation to every endpoint"
slug: "add-input-validation"
category: "api-hardening"
type: "prompt"
tags: ["api", "validation", "zod"]
source: "https://composedsecurity.com/blog/10-security-prompts-for-vibe-coders"
source_label: "Prompt 6"
---

# Add strict input validation to every endpoint

Zod schemas per endpoint, strict parsing, and a dedicated section for authorization-via-input bugs.

> Part of the **API Hardening** pack. From the Composed Security blog: [10 Copy-Paste Security Prompts for Your AI Agent](https://composedsecurity.com/blog/10-security-prompts-for-vibe-coders).

## Prompt

```text
Add strict input validation to every endpoint accepting user input. Use Zod.

Step 1: find every input entrypoint. API routes (App Router, Pages Router, Express, Fastify, Hono). Server actions. tRPC procedures. WebSocket message handlers. Webhook handlers (signature-verified webhooks like Stripe still need body validation). For each: what data it currently accepts (req.body, formData, query params, route params, headers).

Step 2: define a Zod schema per endpoint. Every expected field with correct type. Reasonable bounds: string min/max, number min/max, array length caps. `.email()`, `.url()`, `.uuid()`, `.datetime()` where applicable. `.strict()` so unknown fields are REJECTED, not dropped. Reject empty required fields explicitly.

Step 3: replace direct input access. Before: `const { name, email } = await req.json()`. After: `const parsed = MySchema.safeParse(await req.json()); if (!parsed.success) return Response.json({ error: "invalid_input", details: parsed.error.flatten() }, { status: 400 }); const { name, email } = parsed.data`.

Step 4: FLAG any endpoint reading authorization-controlling fields from request body. user_id, profile_id, owner_id from req.body instead of session. role, isAdmin, tenantId from req.body. price, amount, total accepted from client without server-side recompute. Output these in a separate section "AUTHORIZATION-VIA-INPUT BUGS". Validation alone won't fix them. They need to read from authenticated session, not body. Show the fix.

Step 5: file uploads also validate. File type (magic-byte check, not MIME header). File size cap. Images: dimensions sanity check. PDFs: don't trust filename extensions.

Step 6: output. List of schemas created (file paths). List of endpoints validated. "AUTHORIZATION-VIA-INPUT BUGS" section if any. Test plan: one VALID and one INVALID payload per endpoint, in curl form.

Never strip strictness to "make it work." Legitimate request rejected = schema is wrong. Fix the schema. Don't relax it.
```

## How to use

Paste the block above into your coding agent (Cursor, Claude Code, Codex, Lovable, or Bolt). Give it read access to the repo. Keep it read-only where the prompt says so, and verify each finding before acting on it.

---

Found this useful? [Composed Security](https://composedsecurity.com) reviews your pull requests for exactly this class of bug.
