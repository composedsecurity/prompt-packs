---
title: "Scrub a leaked secret from git history"
slug: "scrub-secrets-from-git-history"
category: "secrets"
type: "prompt"
tags: ["secrets", "git", "incident-response"]
source: "https://composedsecurity.com/blog/10-security-prompts-for-vibe-coders"
source_label: "Prompt 4"
---

# Scrub a leaked secret from git history

A git-filter-repo playbook: revoke first, scrub, verify, force-push, and hunt the copies.

> Part of the **Secrets & Env Vars** pack. From the Composed Security blog: [10 Copy-Paste Security Prompts for Your AI Agent](https://composedsecurity.com/blog/10-security-prompts-for-vibe-coders).

## Prompt

```text
Walk me through scrubbing a committed secret from git history. Order matters.

Inputs: secret-bearing file path: [PATH]. Provider: [PROVIDER].

Step 1, pre-flight (do not skip). Tell me to revoke the secret at [PROVIDER's dashboard URL] and confirm I've done it before continuing. Working tree must be clean (`git status` empty); if not, tell me to commit or stash. Backup the repo: `cp -r repo repo-backup`.

Step 2, scrub with git-filter-repo (NOT BFG; git-filter-repo is GitHub's current recommendation). Show install command for my OS. `git filter-repo --replace-text` invocation that replaces secret with `***REMOVED***` everywhere. If file should be deleted entirely: `git filter-repo --path <path> --invert-paths`. Explain each flag in one short line.

Step 3, verify. `git log --all -p -S'<first 8 chars>'`: confirm zero matches. `git reflog expire --expire=now --all && git gc --prune=now --aggressive`.

Step 4, remote. Warn: this rewrites history; anyone with a clone must re-clone. `git push --force-with-lease origin --all && git push --force-with-lease origin --tags`. Tell me to notify collaborators they MUST re-clone, not pull.

Step 5, hunt the copies (most guides skip this). GitHub Actions/CI logs. GitHub forks (search api.github.com/repos/.../forks; ask each fork owner). Vercel/Netlify build logs. Sentry/observability tools that may have logged it. Slack/Discord/email where I might have shared it. Local clones on other machines. Provider's usage logs (was it used while exposed?).

Step 6, post-checklist. Old secret revoked. New secret generated, stored in env vars. App redeployed. History scrubbed locally. Force-pushed. Collaborators notified. CI/build logs cleared. Provider usage logs reviewed. If unauthorized activity: support ticket opened.

Reminder: scrubbing is necessary but NOT sufficient. The secret MUST be rotated with the provider FIRST. Otherwise bots may already have it.
```

## How to use

Paste the block above into your coding agent (Cursor, Claude Code, Codex, Lovable, or Bolt). Give it read access to the repo. Keep it read-only where the prompt says so, and verify each finding before acting on it.

---

Found this useful? [Composed Security](https://composedsecurity.com) reviews your pull requests for exactly this class of bug.
