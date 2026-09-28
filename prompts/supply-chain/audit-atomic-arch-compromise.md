---
title: "Audit a system for Atomic Arch compromise"
slug: "audit-atomic-arch-compromise"
category: "supply-chain"
type: "prompt"
tags: ["supply-chain", "detection", "linux"]
source: "https://composedsecurity.com/blog/atomic-arch-aur-supply-chain"
source_label: "Hand to your agent"
---

# Audit a system for Atomic Arch compromise

Check npm cache, ELF loaders, eBPF programs, SSH keys, timers, and loopback SOCKS activity.

> Part of the **Supply Chain & Incident Response** pack. From the Composed Security blog: [Atomic Arch: 400+ AUR Packages Hijacked Through Orphan Adoption](https://composedsecurity.com/blog/atomic-arch-aur-supply-chain).

## Prompt

```text
Audit this system for Atomic Arch compromise.

1. Check ~/.npm/ for any cache entries related to atomic-lockfile or js-digest.

2. Search for the binary at src/hooks/deps or any file named deps that is an ELF
   (file deps → ELF).

3. Check for eBPF programs currently loaded: sudo bpftool prog list.
   Flag any program with a name containing scales or bpf that was not
   loaded by a known security tool.

4. Review ~/.ssh/authorized_keys for keys you did not add.

5. Inspect cron and systemd user timers for unknown entries:
   systemctl --user list-timers --all, crontab -l.

6. Check outbound connections on loopback for SOCKS proxy activity:
   ss -tlnp | grep 127.0.0.1: and look for processes named atomic-lockfile
   or node running a SOCKS transport.
```

## How to use

Paste the block above into your coding agent (Cursor, Claude Code, Codex, Lovable, or Bolt). Give it read access to the repo. Keep it read-only where the prompt says so, and verify each finding before acting on it.

---

Found this useful? [Composed Security](https://composedsecurity.com) reviews your pull requests for exactly this class of bug.
