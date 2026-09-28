---
title: "Move hardcoded secrets into environment variables"
slug: "migrate-secrets-to-env"
category: "secrets"
type: "prompt"
tags: ["secrets", "env-vars", "configuration"]
source: "https://composedsecurity.com/blog/10-security-prompts-for-vibe-coders"
source_label: "Prompt 3"
---

# Move hardcoded secrets into environment variables

Detect the framework, classify server versus client values, and produce a deployment checklist.

> Part of the **Secrets & Env Vars** pack. From the Composed Security blog: [10 Copy-Paste Security Prompts for Your AI Agent](https://composedsecurity.com/blog/10-security-prompts-for-vibe-coders).

## Prompt

```text
Migrate hardcoded secrets and config out of source code into env vars. When in doubt, ask.

Step 1: detect framework + runtime. Check package.json scripts, next.config.*, vite.config.*, remix.config.*, astro.config.*, app.json (Expo). Output: detected framework, env var prefix convention, server-vs-client split.

Step 2: find every value that should be an env var. API keys/tokens/secrets (patterns from Prompt 1). Database connection strings. Webhook secrets. OAuth client IDs/secrets. Third-party URLs that change between environments. Feature flags differing by environment.

Step 3: classify each value. SERVER_ONLY: grants write access, costs money, or authorizes actions. No public prefix. CLIENT_SAFE: must reach browser (public Stripe key, Supabase URL/anon key, Maps key). Use framework's public prefix.

Step 4: for each value: new env var name (SCREAMING_SNAKE_CASE, descriptive, framework-conventional); code change as before/after diff; goes in .env.local, .env.example, or both.

Step 5: file changes. `.env.local`: actual secrets (gitignored). `.env.example`: same keys, blank/placeholder values (committed). `.gitignore`: add `.env`, `.env.local`, `.env.*.local`. Replace hardcoded refs with env var lookups using framework idiom.

Step 6: deployment checklist. Table of every var: classification, where to set (Vercel/Netlify/Railway/Fly). Specific dashboard URL paths if host detectable from config. Vars differing between production vs preview.

Flag LOUDLY: public-prefixed vars that look like server secrets (NEXT_PUBLIC_STRIPE_SECRET_KEY) leaking to browser RIGHT NOW; values committed to git history (cross-ref Prompt 1); framework gotchas (Vite needs VITE_; Next.js client components need NEXT_PUBLIC_; server actions don't). Do NOT delete original hardcoded values until I confirm new env vars work locally.
```

## How to use

Paste the block above into your coding agent (Cursor, Claude Code, Codex, Lovable, or Bolt). Give it read access to the repo. Keep it read-only where the prompt says so, and verify each finding before acting on it.

---

Found this useful? [Composed Security](https://composedsecurity.com) reviews your pull requests for exactly this class of bug.
