---
title: "Find every exposed secret in a repo"
slug: "audit-exposed-secrets"
category: "secrets"
type: "prompt"
tags: ["secrets", "audit"]
source: "https://composedsecurity.com/blog/10-security-prompts-for-vibe-coders"
source_label: "Prompt 1"
---

# Find every exposed secret in a repo

A read-only secret audit with provider regexes, redacted output, severity, and a rotation action per finding.

> Part of the **Secrets & Env Vars** pack. From the Composed Security blog: [10 Copy-Paste Security Prompts for Your AI Agent](https://composedsecurity.com/blog/10-security-prompts-for-vibe-coders).

## Prompt

```text
Audit this repository for exposed secrets. Read-only; do not modify files. Scope: tracked files in working tree, untracked files not in .gitignore, last 100 commits of git history (use `git log --all -p -S<pattern>`). Include source, config, env files, dotfiles, JSON/YAML, markdown, shell. Exclude node_modules, .next, dist, build, .git, vendored libs, lockfiles.

Patterns (regex): OpenAI `sk-(?:proj-)?[A-Za-z0-9_-]{20,}`. Anthropic `sk-ant-[A-Za-z0-9_-]{20,}`. Stripe live `(sk|rk|pk)_live_[A-Za-z0-9]{24,}`. Stripe test `(sk|rk|pk)_test_[A-Za-z0-9]{24,}`. AWS access `(AKIA|ASIA)[A-Z0-9]{16}`. AWS secret `(?<![A-Za-z0-9])[A-Za-z0-9/+=]{40}(?![A-Za-z0-9])` (only flag near 'aws','secret','AKIA'). GitHub token `gh[pousr]_[A-Za-z0-9]{36,}`. Google API `AIza[0-9A-Za-z\-_]{35}`. JWT `eyJ[A-Za-z0-9_-]+\.eyJ[A-Za-z0-9_-]+\.[A-Za-z0-9_-]+`. Supabase service role: JWTs near "service_role" or "SUPABASE_SERVICE_ROLE_KEY". Generic high-entropy: string literals 32+ chars matching `[A-Za-z0-9+/=_-]{32,}`, excluding base64 images, hash digests, lockfile integrity fields.

Output as markdown table per match: File, Line, Pattern, Redacted Value, In History?, In .gitignore?, Severity, Action. Redaction: first 6 + last 4 chars only; never paste full secret. If in history but not working tree, mark "history only" (still critical). Severity: CRITICAL is live production keys (sk_live_, AKIA, service_role) in working tree or history. HIGH is test keys, expired-looking patterns, or generic high-entropy clearly a credential. MEDIUM is ambiguous high-entropy near words like "password", "token", "secret".

Action template: CRITICAL/HIGH "Rotate at [provider URL]. Move to env var [SUGGESTED_NAME]. Scrub from history with git-filter-repo." MEDIUM "Investigate. Likely should be env var if real credential." End report with: counts by severity; whether `.env`, `.env.local`, `.env.production` are in `.gitignore`; client-side env vars in use (VITE_, NEXT_PUBLIC_, REACT_APP_, EXPO_PUBLIC_) flagged each as "Shipped to browser. NOT private."; whether to run gitleaks/trufflehog for deeper scan. If uncertain about a match, include and flag for human review.
```

## How to use

Paste the block above into your coding agent (Cursor, Claude Code, Codex, Lovable, or Bolt). Give it read access to the repo. Keep it read-only where the prompt says so, and verify each finding before acting on it.

---

Found this useful? [Composed Security](https://composedsecurity.com) reviews your pull requests for exactly this class of bug.
