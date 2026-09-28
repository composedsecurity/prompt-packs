# Supply Chain & Incident Response

MCP, postinstall, registry, and cloud compromise playbooks.

These are the compromises that do not arrive through your own code: a postinstall hook in a dependency, an MCP server bound to the wrong interface, a poisoned AUR package, or a public bucket with credentials inside. The pack mixes fast detection commands with full incident-response playbooks.

**11 prompts in this pack.** [Back to all packs](../README.md)

## Prompts in this pack

| Prompt | Type | What it does |
|---|---|---|
| [Audit MCP servers for command execution](./audit-mcp-stdio-rce.md) | prompt | Inventory MCP servers, flag public binds and untrusted-input command influence, and check SDK versions against known CVEs. |
| [Sweep for MCP STDIO command execution](./sweep-mcp-stdio-iocs.md) | command | A one-line grep across ~/.claude, ~/.cursor, and .vscode for shell-out patterns in MCP config. |
| [Grep for the postinstall campaign IOCs](./sweep-postinstall-iocs.md) | command | Search manifests, lockfiles, and CI YAML for the campaign's indicators of compromise. |
| [Audit your stack for the postinstall campaign](./audit-postinstall-campaign.md) | prompt | Sweep IOCs, audit lifecycle scripts, disable install scripts, and age out exposed secrets. |
| [Postinstall hook reference (inspect, do not run)](./postinstall-hook-reference.md) | command | The exact malicious postinstall one-liner from the 700-repo campaign, kept for detection comparison. Do not run. |
| [Compromise check for a machine and repo](./compromise-check-machine-repo.md) | prompt | Eight signals across CI logs, lifecycle scripts, run-time anomalies, audit logs, API usage, keys, and dotfiles. |
| [Supply-chain incident response playbook](./supply-chain-incident-response.md) | prompt | Six phases: contain, scope, audit logs, rotate, hunt persistence, notify. |
| [Set a supply-chain hygiene baseline](./hygiene-baseline.md) | prompt | Lockfiles, SHA-pinned Actions, extension audit, gitleaks, and a weekly audit-log review. |
| [Audit a system for Atomic Arch compromise](./audit-atomic-arch-compromise.md) | prompt | Check npm cache, ELF loaders, eBPF programs, SSH keys, timers, and loopback SOCKS activity. |
| [Atomic Arch hook reference (inspect, do not run)](./atomic-arch-hook-reference.md) | command | The malicious preinstall entry from the Atomic Arch campaign, kept for detection comparison. |
| [Audit cloud infrastructure for breach modes](./audit-cloud-infrastructure.md) | prompt | S3 public-access blocks, SCP enforcement, secret rotation, credential reuse, and IR playbook coverage. |

## Recommended order

1. [Audit MCP servers for command execution](./audit-mcp-stdio-rce.md)
2. [Sweep for MCP STDIO command execution](./sweep-mcp-stdio-iocs.md)
3. [Grep for the postinstall campaign IOCs](./sweep-postinstall-iocs.md)
4. [Audit your stack for the postinstall campaign](./audit-postinstall-campaign.md)
5. [Postinstall hook reference (inspect, do not run)](./postinstall-hook-reference.md)
6. [Compromise check for a machine and repo](./compromise-check-machine-repo.md)
7. [Supply-chain incident response playbook](./supply-chain-incident-response.md)
8. [Set a supply-chain hygiene baseline](./hygiene-baseline.md)
9. [Audit a system for Atomic Arch compromise](./audit-atomic-arch-compromise.md)
10. [Atomic Arch hook reference (inspect, do not run)](./atomic-arch-hook-reference.md)
11. [Audit cloud infrastructure for breach modes](./audit-cloud-infrastructure.md)

## How to use this pack

The `sweep-*` and `*-reference` files are commands or indicators: read them, point them at the right target, and do not run a reference hook. The prompts are for handing to an agent when you are checking or responding.

## From the blog

These prompts are explained in full in the posts below. The post is where you get the failure mode, the reasoning, and the edge cases; the prompt is what you run.

- [Your MCP server is a shell. Anthropic calls it expected.](https://composedsecurity.com/blog/mcp-stdio-rce)
- [700 repos. One postinstall hook.](https://composedsecurity.com/blog/postinstall-hook-700-repos)
- [GitHub got popped. Grafana too. Here's the playbook for everyone else.](https://composedsecurity.com/blog/github-grafana-popped-supply-chain-playbook)
- [Atomic Arch: 400+ AUR Packages Hijacked Through Orphan Adoption](https://composedsecurity.com/blog/atomic-arch-aur-supply-chain)
- [12,000 Passwords. All the Same One.](https://composedsecurity.com/blog/fulcrumsec-global-schools-breach)

## Related

- [All prompt packs](../README.md)
- [Secrets & Env Vars](../secrets/README.md)
- [Database](../database/README.md)
- [Authentication & Access Control](../authentication/README.md)
- [API Hardening](../api-hardening/README.md)
- [Release Gate](../release/README.md)
- [Prompt Injection & Agent Authorization](../prompt-injection/README.md)
- [Agent Runtime & Model Harnesses](../agent-runtime/README.md)
- [Composed Security blog](https://composedsecurity.com/blog)
