---
layout: post
title: How I'd Break Into Your Business (And the Five Things That Would Stop Me)
tags: [hardening, attacker mindset, fundamentals]
author: Alex Dalzell
---

I break into computer systems for a living — legally, with permission, so that the results land on a report instead of the news. After enough of this, you notice something: the ways in are boringly consistent. It's rarely a movie-style genius hack. It's almost always a handful of small, fixable weaknesses that nobody got around to closing.

So let me walk you through how I'd approach your business, and — more importantly — the specific thing that stops each step. No exploit code here. Just the attacker's map, and where the roadblocks go.

### Step 1: I find the door you forgot was unlocked

The first thing I look for is anything of yours facing the internet: a remote-access login, an old web portal, a VPN appliance, a mail server. Every one of these is a door, and the ones that don't get patched are the ones I love. A known weakness in an unpatched appliance is often all it takes.

**What stops me:** Keeping internet-facing systems patched, and knowing what you even have exposed. You can't defend a door you forgot exists.

### Step 2: I guess (or steal) a password

If the door is locked, I try the keys. People reuse passwords, pick weak ones, and get tricked into typing them into fake login pages. A surprising amount of "hacking" is just logging in with credentials that were never protected properly.

**What stops me:** Multi-factor authentication (MFA). This is the highest-value security control a small business can turn on, full stop. Even if I have your password, MFA means I still can't get in. If you do one thing after reading this, make it this.

### Step 3: I trick a human

If the technology holds, I go after people. A convincing email, a fake invoice, a phone call pretending to be IT. Humans are helpful by nature, and attackers weaponize that.

**What stops me:** A team that's been taught to pause on anything involving money, credentials, or urgency — and a culture where double-checking a weird request is encouraged, not seen as paranoid.

### Step 4: I move from one machine to the whole network

Once I'm on a single machine, I want everything. On most networks, getting from one workstation to the server and the backups is far too easy — because everything can talk to everything (see: my post on network segmentation).

**What stops me:** Segmentation, and not handing every user administrator rights. If the compromised account can't reach the valuable systems, my foothold is nearly worthless.

### Step 5: I hold your data hostage

The payday for a lot of attackers is ransomware: encrypt everything, demand payment. What makes this survivable or fatal is entirely down to one thing.

**What stops me:** Backups that actually work and that I can't reach or encrypt. Backups stored offline or in a separate account, tested regularly so you know they'll restore. With good backups, ransomware is an expensive bad week. Without them, it's the end of the business.

### The pattern

Notice what's *not* on this list: exotic tools, zero-day exploits, nation-state wizardry. The five things that would actually stop me are patching, MFA, trained people, segmentation, and working backups. None of them are expensive. All of them are within reach of a business with no dedicated security staff.

That's the real message here. The gap between "easy target" and "not worth the effort" is smaller than most owners think — but only if you close it before someone comes knocking.

**Takeaway:** Attackers follow a predictable path. Patch your exposed systems, turn on MFA, train your people, segment your network, and keep working backups. Do those five things and you've defeated the overwhelming majority of real-world attacks.
