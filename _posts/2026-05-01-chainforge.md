---
layout: post
title: Why I Built My Own Exploit-Development Tool Instead of Using Someone Else's
tags: [tooling, exploit development, ChainForge, craft]
author: Alex Dalzell
---

This one's a little more inside-baseball than my usual posts. It's less "here's what your business should do" and more "here's how the person you might hire actually works." If you want to know whether a security professional understands their craft deeply or just runs other people's scripts, posts like this are how you tell. So: here's a tool I built, and why.

### The problem

Part of advanced exploit development involves something called a **ROP chain** — a technique for getting code to run on a system that has defenses specifically designed to prevent exactly that. Building one is like assembling a sentence out of tiny fragments scattered across a program's code, where each fragment does one small thing, and you have to string them together in precisely the right order to achieve your goal.

The catch: there can be tens of thousands of these fragments, many of them unusable because they contain "bad bytes" that break the exploit, and finding the right ones by hand is tedious, error-prone, grind work. The existing ways of doing it left me flipping between tools and tracking too much in my own head.

### The tool

So I built **ChainForge** — a terminal-based tool that does this hunting for me. ([It's open source on GitHub](https://github.com/nanoby7e/ChainForge).) I wrote it in pure Python with no external dependencies, originally to support my work through the OffSec EXP-301 exploit-development course.

The idea was to put every repetitive question I kept asking into one workspace: *What can this code actually do? Can I move this value into that place? Does my chain contain any bad bytes that would break it?* Instead of answering those by hand every time, ChainForge answers them instantly — and it's aware of the bad-byte constraints throughout, so it automatically filters out anything that wouldn't work.

### The part I care about most

Here's what I want you to take from this, whether or not a single word of the above made sense: **I tested it.**

ChainForge ships with a test suite that validates the tool against real data across five layers of checks — confirming that what it reports actually matches reality, that its results are consistent, and that saving and reloading your work never corrupts it. I built that because a tool that gives you confidently wrong answers is worse than no tool at all.

I also cared about how it *feels* to use. Clean output, clear indicators, no clutter — because a tool you fight with is a tool you make mistakes with.

That mindset — build the right thing, verify it works, sweat the details — is exactly what I bring to securing a business. The subject matter changes. The rigor doesn't.

**Takeaway:** The person you trust with your security should understand their tools deeply enough to build and test their own when the existing ones fall short. That's the difference between someone who runs a scan and someone who knows what the scan is actually doing.
