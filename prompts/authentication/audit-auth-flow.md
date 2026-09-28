---
title: "Audit an authentication flow"
slug: "audit-auth-flow"
category: "authentication"
type: "prompt"
tags: ["auth", "audit"]
source: "https://composedsecurity.com/blog/10-security-prompts-for-vibe-coders"
source_label: "Prompt 7"
---

# Audit an authentication flow

A CRITICAL/HIGH/MEDIUM review of token storage, session verification, OAuth state, and rate limits.

> Part of the **Authentication & Access Control** pack. From the Composed Security blog: [10 Copy-Paste Security Prompts for Your AI Agent](https://composedsecurity.com/blog/10-security-prompts-for-vibe-coders).

## Prompt

```text
Security-audit this app's authentication flow. Read-only.

Detect the auth stack first. Library: Supabase Auth, Clerk, Auth0, Firebase Auth, NextAuth/Auth.js, Lucia, custom? Token storage: cookie, localStorage, sessionStorage? Session verification: middleware, per-route, client-side only?

For every finding output: severity (CRITICAL/HIGH/MEDIUM), file:line, why it's a problem, exact fix.

CRITICAL: tokens in localStorage/sessionStorage (vulnerable to XSS exfiltration; should be httpOnly cookies). Session verification only frontend (attackers bypass with one fetch; server must verify every request). Privileged routes without server-side session checks (admin panel, billing, account deletion). Routes reading `user_id`/`role`/`isAdmin` from request body for authorization. Custom JWT signing/verification with missing/weak/hardcoded secret. Password reset that doesn't expire tokens, doesn't rate-limit, or sends token in URL parameter. OAuth callbacks not validating `state` (CSRF on OAuth). "Remember me" using long-lived non-rotating tokens.

HIGH: email/password change without re-authentication. Account enumeration via login error messages ("user not found" vs "wrong password"). Missing CSRF protection on cookie-auth state-changing endpoints (POST/PUT/DELETE). Sessions that don't rotate on privilege change (e.g., promoted to admin while logged in). Missing rate limits on /login, /signup, /reset-password (use Prompt 5's AUTH_SENSITIVE). Logout that only clears client state (server must invalidate session too).

MEDIUM: password requirements weaker than 12 chars or no breach-list check. No MFA option for admin users. Sensitive operations (delete account, change email) without email confirmation. Session cookies missing Secure, HttpOnly, SameSite=Lax/Strict. CORS allowing credentials AND wildcard origins.

Output: markdown table | Severity | Check # | File:Line | Description | Fix |. End with one-line verdict: "GO" or "NO-GO" + gating findings. Do not modify code.
```

## How to use

Paste the block above into your coding agent (Cursor, Claude Code, Codex, Lovable, or Bolt). Give it read access to the repo. Keep it read-only where the prompt says so, and verify each finding before acting on it.

---

Found this useful? [Composed Security](https://composedsecurity.com) reviews your pull requests for exactly this class of bug.
