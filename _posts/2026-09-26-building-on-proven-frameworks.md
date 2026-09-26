---
layout: post
title: Building Tools on Proven Frameworks: Why Reinventing the Wheel is a Trap
tags: [tool-building, frameworks, architecture, efficiency]
author: Alex Dalzell
---

When you're building offensive or defensive security tooling, the temptation is immediate: start from scratch, build exactly what you want, no legacy baggage. It's seductive. But it's also where most tool projects die—buried under months of protocol implementation, edge-case handling, and the realization that you've built a lower-quality version of something that already exists.

I learned this building a Windows offensive-security toolkit. The naive approach would have been to implement SMB, RPC, WMI, DCOM, WinRM from the ground up. Just the protocol work alone is a year of engineering. Instead, I made a different choice: vendor an existing framework and build the operator experience on top of it.

That decision changed everything about the project's viability.

## The Real Cost of Protocol Implementation

Before you implement a Windows protocol, understand what you're signing up for:

- **SMB** isn't just a file-sharing protocol. It's signing, encryption, session setup, dialect negotiation, share enumeration. It's updated every few years with new features. It's got edge cases around anonymous sessions, encryption modes, and dialect fallback that bite you in production.

- **RPC** isn't one protocol—it's a foundation for dozens of others (WMI, DCOM, Task Scheduler, Remote Registry). Each has its own marshalling rules, its own stubs, its own version history. The marshalling—NDR32 vs NDR64—is a rabbit hole. One wrong bit and the whole thing fails silently.

- **WinRM** is WSMan over HTTP/HTTPS with channel binding and message encryption. The spec is massive. The Windows implementation has quirks. You don't just "do WinRM"—you spend a month learning what you don't know about it.

- **Kerberos** authentication is a multi-round negotiation with ticket caching, delegation, and encryption types. It's the future of Windows auth and the most fragile part of most tools because so few people implement it correctly.

Every one of these is a permanent tax on your project. A new Windows version comes out, your code breaks. A security advisory drops, you have to understand the implications for your implementation. You're not building the tool anymore—you're maintaining a protocol library.

That's the trap.

## The Framework Bet

The alternative is finding a maintained framework that already solved this—and then betting on it. This requires three things:

**First, the framework has to be good enough.** Not perfect, not feature-complete for everything. Just good enough to solve the hard problems you don't want to solve. A solid framework handles the transport layer, the auth mechanisms, the protocol quirks. It handles 80% of the complexity. The remaining 20%—the operator experience, the logging, the output formatting, the module pattern—is where the value lives.

**Second, it has to be maintained.** A framework is only useful if it keeps pace with the platform it abstracts. When Windows changes, when new attack surface appears, when a bug is found, it gets fixed. You pull the update, run your regression tests, and move on. Dead frameworks are worse than no framework—they're anchors.

**Third, you have to be willing to vendor it and never fork it.** This is the discipline part. You don't edit the framework's code. You don't "just fix this one thing" and diverge. You consume it as a dependency. If it lacks something you need, you build it in your tool, on top of the framework. This keeps your upgrade path clean. When you pull a new version of the framework, nothing in your codebase breaks because you haven't modified it.

## What This Buys You

By standing on a proven framework, you get:

**Speed to value.** You don't spend a year on protocol implementation. You spend weeks on the operator experience: output formatting, logging, multi-host sweep, credential capture, obfuscation. The parts that actually matter for users.

**Correctness you can't afford.** The edge cases in SMB signing, RPC marshalling, Kerberos negotiation—they're in the framework. They're tested. They're the result of years of real-world work. You don't get that by reimplementing from scratch.

**Upgrade path clarity.** When the framework updates, your decision tree is simple: does my regression test pass? If yes, you're done. If no, you debug one layer (your code or the framework?), fix it, and move on. You don't have to understand every line of protocol implementation because you didn't write it.

**Modularity as a freebie.** Because the framework handles the cross-cutting concerns (auth, transport, protocol specifics), your tool code is thin. A new module is just the technique-specific logic plus a thin wrapper that plugs into the framework's pattern. That's where the leverage lives.

**Focus on differentiation.** Your job isn't to out-implement the protocol maintainers. It's to build something they can't: an operator-focused experience. Better logging. Cleaner output. Faster multi-host sweeps. Integrated workflow. That's where you win.

## The Cost

Standing on a framework isn't free. You're dependent on its pace. If the maintainers deprioritize your use case, you're stuck. If a new protocol becomes critical and the framework doesn't support it, you have to wait or fork. If the framework takes a direction you disagree with, you're either along for the ride or you're maintaining a fork (which defeats the purpose).

These are real constraints. But they're almost always better than the alternative: maintaining your own protocol library while also building a tool.

## The Bet

When building a tool on frameworks, you're betting that:

1. The framework will stay maintained.
2. Its scope stays aligned with your needs.
3. Your operator experience innovations are worth more than the constraint of framework dependency.

That bet usually pays off. You build in a fraction of the time. The code is cleaner because the framework handles the cross-cutting concerns. Updates are straightforward. And when new capability emerges, you add it by wrapping the framework's capabilities, not by reimplementing from scratch.

## The Principle

The broader lesson: **don't solve problems that are already solved.** Find the framework, the library, the platform that solves the hard part of your problem. Then build your differentiation on top of it.

Your tool is not valuable because you implemented the protocol correctly. It's valuable because you built an operator experience, a workflow, an abstraction that nobody else has. Stand on the shoulders of maintained frameworks and you free yourself to focus on that.

For security tooling, for infrastructure code, for almost anything complex: identify the layer you're actually trying to innovate on. Build on proven foundations below it. That's how you ship fast and don't get buried.
