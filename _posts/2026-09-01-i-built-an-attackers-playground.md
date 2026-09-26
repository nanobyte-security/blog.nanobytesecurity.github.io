---
layout: post
title: I Built an Attacker's Playground. Here's What It Taught Me About Your Network.
tags: [network segmentation, lab, defense]
author: Alex Dalzell
---

Most small businesses run what I'd politely call a "flat" network. Every device — the receptionist's PC, the accounting laptop, the security cameras, the server holding your customer data — sits on the same slice of the network and can talk to everything else. It works. It's cheap. And it's the single biggest reason a small compromise turns into a company-ending one.

I don't say that to scare you. I say it because I spend my time building networks specifically so I can break into them, and the flat network is the gift that keeps on giving for anyone doing what I do.

### The lab

To practice attacks safely and legally, I built a self-contained lab — a miniature company network that exists only to be attacked. Nothing in it is real, nothing connects to a client, and no actual business data ever touches it. That's the whole point: it lets me demonstrate real techniques without putting anyone at risk.

The lab is split into three separate zones:

- **Servers** — where the "important" machines live.
- **Workstations** — the everyday user machines.
- **Red team** — my attacker's foothold, kept apart from everything else.

Building it meant working through the same plumbing a real network relies on: routing between zones, address assignment across subnets, and the rules that decide which zone is allowed to talk to which. The infrastructure was deployed from code so I can tear the whole thing down and rebuild it identically in minutes.

[Insert network diagram: three subnets with the firewall/router in the middle]

### The lesson

Here's the part that matters for you. In the lab, when I land on a workstation — say, through a user who opened the wrong attachment — the first thing I do is look around. *What else can I reach from here?*

On a flat network, the answer is "everything." One clicked link and I can see the server, the backups, the cameras, the lot. My job becomes trivial.

On a segmented network, the answer is "almost nothing." I'm stuck on the workstation zone, and to get anywhere valuable I have to punch through the boundary between zones — which is loud, slow, and gives your defenses a chance to notice. Segmentation doesn't stop the initial mistake. It stops the mistake from becoming a catastrophe.

### What to actually do about it

You don't need a lab or a security team to benefit from this. You need to separate the things that matter from the things that get compromised:

1. **Put untrusted devices on their own zone.** Guest Wi-Fi, security cameras, smart TVs, and IoT gadgets should never share a network with your business machines. Most business-grade routers and access points support a separate VLAN or guest network for exactly this — it's often a checkbox.
2. **Isolate the crown jewels.** Your server, your accounting system, your customer database — these should live somewhere that a random workstation can't freely reach.
3. **Default to "no."** The zones should only be allowed to talk to each other where there's a real reason. Everything else stays blocked.

If that sounds like more than your current setup can handle, that's a useful thing to learn *now* rather than during an incident. Segmentation is one of the highest-value, lowest-cost improvements a small business can make, and it's the first thing I wish more of the networks I test actually had.

**Takeaway:** A flat network turns a single mistake into a total loss. Separating your network into zones is cheap, often just a configuration change, and it's the difference between "we had an incident" and "we had a disaster."

Want to know how far an attacker could get on your network today? That's exactly what a penetration test answers. [Get in touch](mailto:alex@nanobytesecurity.com), or [book a call](https://calendly.com/alex-nanobytesecurity/30min).]

**Takeaway:** Attackers follow a predictable path. Patch your exposed systems, turn on MFA, train your people, segment your network, and keep working backups. Do those five things and you've defeated the overwhelming majority of real-world attacks.
