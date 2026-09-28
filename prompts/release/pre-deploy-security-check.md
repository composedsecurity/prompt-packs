---
title: "Pre-deployment security go/no-go check"
slug: "pre-deploy-security-check"
category: "release"
type: "prompt"
tags: ["release", "checklist", "go-no-go"]
source: "https://composedsecurity.com/blog/10-security-prompts-for-vibe-coders"
source_label: "Prompt 10"
---

# Pre-deployment security go/no-go check

Twenty-seven checks across secrets, database, auth, API, payments, access control, infrastructure, and hygiene.

> Part of the **Release Gate** pack. From the Composed Security blog: [10 Copy-Paste Security Prompts for Your AI Agent](https://composedsecurity.com/blog/10-security-prompts-for-vibe-coders).

## Prompt

```text
Final pre-deployment security check. One CRITICAL fail = NO-GO. Output markdown table: # | Category | Severity | Status | Detail | Fix |.

Secrets & env (use Prompt 1 if needed). 1. CRITICAL: no hardcoded secrets in source files. 2. CRITICAL: no secrets in last 100 commits of git history. 3. CRITICAL: `.gitignore` covers `.env`, `.env.local`, `.env.*.local`. 4. HIGH: every public-prefixed env var (NEXT_PUBLIC_, VITE_) is safe to expose to browser. 5. HIGH: `.env.example` exists, documents every required env var.

Database (use Prompt 2 if needed). 6. CRITICAL: RLS enabled on every Supabase/Firebase user-data table. 7. CRITICAL: RLS policies actually restrict access (no `USING (true)` on user-owned tables). 8. HIGH: service role / admin keys referenced ONLY in server-side code.

Auth (use Prompt 7 if needed). 9. CRITICAL: session tokens in httpOnly cookies, not localStorage/sessionStorage. 10. CRITICAL: server-side session verification on every protected route. 11. HIGH: no handlers reading `user_id`/`role` from request body for authorization. 12. HIGH: login, signup, password-reset endpoints rate-limited.

API safety (use Prompts 5+6 if needed). 13. CRITICAL: every endpoint accepting user input validates with Zod or equivalent. 14. CRITICAL: rate limiting on every endpoint calling a paid third-party API. 15. HIGH: CORS set to specific origin(s), not `*`, on routes accepting credentials.

Payments (use Prompt 8; mark N/A if no payments). 16. CRITICAL: Stripe webhook handlers verify `stripe-signature`. 17. CRITICAL: Stripe secret key (sk_*) used only server-side. 18. HIGH: webhook handlers idempotent on event ID.

Access control (use Prompt 9 if needed). 19. CRITICAL: every frontend authorization check has matching backend enforcement. 20. HIGH: no endpoint accepting `userId` parameter (which user to act on) except endpoints explicitly admin-only.

Infrastructure. 21. HIGH: production HTTPS only. 22. HIGH: cookie flags Secure, HttpOnly, SameSite=Lax (Strict for sensitive). 23. MEDIUM: Sentry/equivalent scrubs PII. 24. MEDIUM: no source maps in production OR uploaded privately to error monitoring.

Code hygiene. 25. MEDIUM: no `console.log` of secrets, tokens, or user PII in production. 26. MEDIUM: no TODO/FIXME/XXX referencing security gaps. 27. LOW: dependencies current.

Reporting. Every FAIL: file:line + concrete fix. Every N/A: explain why. Severity-weighted summary: # CRITICAL fails, # HIGH, # MEDIUM, # LOW. Final verdict on its own line: "GO ✅" or "NO-GO ❌, fix CRITICAL items first". Do NOT modify files. Read-only audit. Can't determine something with confidence? Mark FAIL, explain what would need to be true for PASS.
```

## How to use

Paste the block above into your coding agent (Cursor, Claude Code, Codex, Lovable, or Bolt). Give it read access to the repo. Keep it read-only where the prompt says so, and verify each finding before acting on it.

---

Found this useful? [Composed Security](https://composedsecurity.com) reviews your pull requests for exactly this class of bug.
