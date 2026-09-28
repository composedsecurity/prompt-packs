# Prompt Packs

> The security prompts from the [Composed Security blog](https://composedsecurity.com/blog), kept here as copy-paste files. Every prompt links back to the post that explains the real-world failure it defends against.

Battle-tested security prompts and detection commands for teams building software with AI coding agents.

Every prompt in this repo is engineered for an agent: explicit scope, regex patterns, output format specs, and edge-case handling. They come from the write-ups on the [Composed Security blog](https://composedsecurity.com/blog), where each one ships with the story of the real-world failure it defends against.

- **Copy and paste** a prompt into Cursor, Claude Code, Codex, Lovable, or Bolt.
- **Keep it read-only** where the prompt says so, and verify each finding.
- **Link back** to the sourcing post for the full context.

## Featured pack: 10 Security Prompts for Vibe Coders

The fastest way to start. Ten copy-paste prompts that audit secrets, add RLS, scrub git history, rate limit, validate input, harden auth, verify Stripe webhooks, and run a pre-deploy go/no-go.

Read the guide: **[10 Copy-Paste Security Prompts for Your AI Agent](https://composedsecurity.com/blog/10-security-prompts-for-vibe-coders)**

| # | Prompt | Category |
|---|---|---|
| 1 | [Find every exposed secret in a repo](prompts/secrets/audit-exposed-secrets.md) | Secrets & Env Vars |
| 2 | [Add Row Level Security to every Supabase table](prompts/database/add-supabase-rls.md) | Database |
| 3 | [Move hardcoded secrets into environment variables](prompts/secrets/migrate-secrets-to-env.md) | Secrets & Env Vars |
| 4 | [Scrub a leaked secret from git history](prompts/secrets/scrub-secrets-from-git-history.md) | Secrets & Env Vars |
| 5 | [Add rate limiting to every API route](prompts/api-hardening/add-rate-limiting.md) | API Hardening |
| 6 | [Add strict input validation to every endpoint](prompts/api-hardening/add-input-validation.md) | API Hardening |
| 7 | [Audit an authentication flow](prompts/authentication/audit-auth-flow.md) | Authentication & Access Control |
| 8 | [Verify Stripe webhook signatures](prompts/api-hardening/verify-stripe-webhooks.md) | API Hardening |
| 9 | [Find frontend-only access controls](prompts/authentication/audit-frontend-only-authz.md) | Authentication & Access Control |
| 10 | [Pre-deployment security go/no-go check](prompts/release/pre-deploy-security-check.md) | Release Gate |

## All prompts by category

### Secrets & Env Vars

Find, move, and permanently scrub credentials.

| Prompt | Type | Source post |
|---|---|---|
| [Find every exposed secret in a repo](prompts/secrets/audit-exposed-secrets.md) | prompt | [10 Copy-Paste Security Prompts for Your AI Agent](https://composedsecurity.com/blog/10-security-prompts-for-vibe-coders) |
| [Move hardcoded secrets into environment variables](prompts/secrets/migrate-secrets-to-env.md) | prompt | [10 Copy-Paste Security Prompts for Your AI Agent](https://composedsecurity.com/blog/10-security-prompts-for-vibe-coders) |
| [Scrub a leaked secret from git history](prompts/secrets/scrub-secrets-from-git-history.md) | prompt | [10 Copy-Paste Security Prompts for Your AI Agent](https://composedsecurity.com/blog/10-security-prompts-for-vibe-coders) |

### Database

Row Level Security and data-access guardrails.

| Prompt | Type | Source post |
|---|---|---|
| [Add Row Level Security to every Supabase table](prompts/database/add-supabase-rls.md) | prompt | [10 Copy-Paste Security Prompts for Your AI Agent](https://composedsecurity.com/blog/10-security-prompts-for-vibe-coders) |

### Authentication & Access Control

Audit logins and move authorization server-side.

| Prompt | Type | Source post |
|---|---|---|
| [Audit an authentication flow](prompts/authentication/audit-auth-flow.md) | prompt | [10 Copy-Paste Security Prompts for Your AI Agent](https://composedsecurity.com/blog/10-security-prompts-for-vibe-coders) |
| [Find frontend-only access controls](prompts/authentication/audit-frontend-only-authz.md) | prompt | [10 Copy-Paste Security Prompts for Your AI Agent](https://composedsecurity.com/blog/10-security-prompts-for-vibe-coders) |

### API Hardening

Rate limits, input validation, and payment webhooks.

| Prompt | Type | Source post |
|---|---|---|
| [Add rate limiting to every API route](prompts/api-hardening/add-rate-limiting.md) | prompt | [10 Copy-Paste Security Prompts for Your AI Agent](https://composedsecurity.com/blog/10-security-prompts-for-vibe-coders) |
| [Add strict input validation to every endpoint](prompts/api-hardening/add-input-validation.md) | prompt | [10 Copy-Paste Security Prompts for Your AI Agent](https://composedsecurity.com/blog/10-security-prompts-for-vibe-coders) |
| [Verify Stripe webhook signatures](prompts/api-hardening/verify-stripe-webhooks.md) | prompt | [10 Copy-Paste Security Prompts for Your AI Agent](https://composedsecurity.com/blog/10-security-prompts-for-vibe-coders) |

### Release Gate

The pre-deployment go/no-go check.

| Prompt | Type | Source post |
|---|---|---|
| [Pre-deployment security go/no-go check](prompts/release/pre-deploy-security-check.md) | prompt | [10 Copy-Paste Security Prompts for Your AI Agent](https://composedsecurity.com/blog/10-security-prompts-for-vibe-coders) |

### Prompt Injection & Agent Authorization

Stop untrusted text from becoming privileged action.

| Prompt | Type | Source post |
|---|---|---|
| [Audit an agentic app as an authorization system](prompts/prompt-injection/audit-agentic-authorization.md) | prompt | [Muse Rebuilt OpenClaw's Shape. The Prompt Injection Came With It.](https://composedsecurity.com/blog/meta-muse-openclaw-prompt-injection) |
| [Detect a pack-hunt jailbreak session](prompts/prompt-injection/detect-pack-hunt-session.md) | prompt | [Anthropic's Safest Model Lasted 24 Hours](https://composedsecurity.com/blog/claude-fable-5-jailbreak) |
| [IR runbook for a pack-hunt jailbreak](prompts/prompt-injection/ir-pack-hunt-session.md) | prompt | [Anthropic's Safest Model Lasted 24 Hours](https://composedsecurity.com/blog/claude-fable-5-jailbreak) |
| [Harden a pipeline against pack hunts](prompts/prompt-injection/audit-pack-hunt-hardening.md) | prompt | [Anthropic's Safest Model Lasted 24 Hours](https://composedsecurity.com/blog/claude-fable-5-jailbreak) |
| [Audit indirect prompt injection in operational text](prompts/prompt-injection/audit-operational-text-injection.md) | prompt | [Logs are hostile input now.](https://composedsecurity.com/blog/fake-sentry-alert-prompt-injection) |
| [Harden agents against indirect prompt injection](prompts/prompt-injection/harden-indirect-prompt-injection.md) | prompt | [Logs are hostile input now.](https://composedsecurity.com/blog/fake-sentry-alert-prompt-injection) |
| [Audit a support agent's privileged actions](prompts/prompt-injection/audit-privileged-agent-actions.md) | prompt | [Hackers asked Meta's AI for Instagram accounts. It said yes.](https://composedsecurity.com/blog/meta-ai-instagram-account-takeover) |
| [Harden a support agent against privileged-action abuse](prompts/prompt-injection/harden-privileged-agent-actions.md) | prompt | [Hackers asked Meta's AI for Instagram accounts. It said yes.](https://composedsecurity.com/blog/meta-ai-instagram-account-takeover) |

### Agent Runtime & Model Harnesses

Detect and contain emergent multi-agent behavior.

| Prompt | Type | Source post |
|---|---|---|
| [Detect agent-collective activity in your logs](prompts/agent-runtime/detect-agent-collective-logs.md) | prompt | [Agent takeover happened. By accident.](https://composedsecurity.com/blog/openai-ai-agents-huggingface-breach) |
| [Audit a training harness for agent collaboration](prompts/agent-runtime/audit-training-harness.md) | prompt | [Agent takeover happened. By accident.](https://composedsecurity.com/blog/openai-ai-agents-huggingface-breach) |
| [Incident response runbook for agent collectives](prompts/agent-runtime/ir-agent-collective.md) | prompt | [Agent takeover happened. By accident.](https://composedsecurity.com/blog/openai-ai-agents-huggingface-breach) |

### Supply Chain & Incident Response

MCP, postinstall, registry, and cloud compromise playbooks.

| Prompt | Type | Source post |
|---|---|---|
| [Sweep for MCP STDIO command execution](prompts/supply-chain/sweep-mcp-stdio-iocs.md) | command | [Your MCP server is a shell. Anthropic calls it expected.](https://composedsecurity.com/blog/mcp-stdio-rce) |
| [Audit MCP servers for command execution](prompts/supply-chain/audit-mcp-stdio-rce.md) | prompt | [Your MCP server is a shell. Anthropic calls it expected.](https://composedsecurity.com/blog/mcp-stdio-rce) |
| [Postinstall hook reference (inspect, do not run)](prompts/supply-chain/postinstall-hook-reference.md) | command | [700 repos. One postinstall hook.](https://composedsecurity.com/blog/postinstall-hook-700-repos) |
| [Grep for the postinstall campaign IOCs](prompts/supply-chain/sweep-postinstall-iocs.md) | command | [700 repos. One postinstall hook.](https://composedsecurity.com/blog/postinstall-hook-700-repos) |
| [Audit your stack for the postinstall campaign](prompts/supply-chain/audit-postinstall-campaign.md) | prompt | [700 repos. One postinstall hook.](https://composedsecurity.com/blog/postinstall-hook-700-repos) |
| [Compromise check for a machine and repo](prompts/supply-chain/compromise-check-machine-repo.md) | prompt | [GitHub got popped. Grafana too. Here's the playbook for everyone else.](https://composedsecurity.com/blog/github-grafana-popped-supply-chain-playbook) |
| [Supply-chain incident response playbook](prompts/supply-chain/supply-chain-incident-response.md) | prompt | [GitHub got popped. Grafana too. Here's the playbook for everyone else.](https://composedsecurity.com/blog/github-grafana-popped-supply-chain-playbook) |
| [Set a supply-chain hygiene baseline](prompts/supply-chain/hygiene-baseline.md) | prompt | [GitHub got popped. Grafana too. Here's the playbook for everyone else.](https://composedsecurity.com/blog/github-grafana-popped-supply-chain-playbook) |
| [Atomic Arch hook reference (inspect, do not run)](prompts/supply-chain/atomic-arch-hook-reference.md) | command | [Atomic Arch: 400+ AUR Packages Hijacked Through Orphan Adoption](https://composedsecurity.com/blog/atomic-arch-aur-supply-chain) |
| [Audit a system for Atomic Arch compromise](prompts/supply-chain/audit-atomic-arch-compromise.md) | prompt | [Atomic Arch: 400+ AUR Packages Hijacked Through Orphan Adoption](https://composedsecurity.com/blog/atomic-arch-aur-supply-chain) |
| [Audit cloud infrastructure for breach modes](prompts/supply-chain/audit-cloud-infrastructure.md) | prompt | [12,000 Passwords. All the Same One.](https://composedsecurity.com/blog/fulcrumsec-global-schools-breach) |

## Repository layout

```text
prompts/
  secrets/
  database/
  authentication/
  api-hardening/
  release/
  prompt-injection/
  agent-runtime/
  supply-chain/
```

Each file carries YAML frontmatter with its category, tags, and the blog post it came from. The prompt itself is always in a single fenced `text` block so it can be copied cleanly.

## Using these in your own work

These prompts are meant to be pasted at an AI coding agent, not run as software. A good workflow:

1. Open the post that matches your worry to understand the failure mode.
2. Open the prompt file and copy the fenced block.
3. Paste it at your agent with the repo in context.
4. Treat the output as leads. Verify before you ship or rotate anything.

## Contributing

Found a prompt that catches something real, or a gap in one? Open an issue or a pull request. Keep the format: scoped, read-only by default, explicit output, and linked to a source post.

## License

MIT. See [LICENSE](./LICENSE).
