---
layout: post
title: Compliance Is the Starting Line, Not the Finish
tags: [compliance, security testing]
author: Alex Dalzell
---

Every organization that takes security seriously eventually runs into a framework. SOC 2, CMMC, HIPAA, PCI DSS — the acronyms pile up fast, and for good reason. Compliance gives you structure, a common language, and a checklist that forces conversations most teams would otherwise keep putting off. It is a genuinely good place to start.

The problem is that too many organizations treat the audit as the destination. They pass, they frame the certificate, and they move on. But compliance locks the front doors. It rarely checks whether the windows are open.

## What compliance actually does well

A framework earns its keep. It makes you inventory what you have, document who can touch it, and prove you have basic controls in place. It gives leadership a reason to fund security work that would otherwise lose to the next feature deadline. And it gives customers and partners a reasonable baseline of trust.

If you have never been through an audit, your first one will almost certainly find real gaps worth fixing. That value is real. Just don't mistake it for the whole picture.

## The common frameworks, briefly

For US-based companies, these are the ones you'll run into most:

- **SOC 2** — The default for SaaS and service providers. Audits your controls against five "trust services criteria" (security, availability, processing integrity, confidentiality, privacy). Flexible, which is both its strength and its weakness.
- **CMMC** — Required for Department of Defense contractors and the defense supply chain. Built on NIST SP 800-171. Tiered levels based on how sensitive the data you handle is.
- **HIPAA** — Protects health information. Applies to healthcare providers, insurers, and anyone handling patient data on their behalf. Heavy on access control, auditing, and breach notification.
- **PCI DSS** — Mandatory if you store, process, or transmit payment card data. Prescriptive and detailed compared to most frameworks.
- **NIST SP 800-171 / NIST CSF** — 800-171 governs controlled unclassified information for federal contractors; the Cybersecurity Framework is a broader, voluntary model many organizations adopt as a backbone.
- **ISO 27001** — The international standard for information security management. Common when you do business globally.
- **FedRAMP** — The bar for cloud services sold to federal agencies. Rigorous and expensive, but the price of entry for that market.
- **GLBA** — Governs how financial institutions protect customer financial data.

Most organizations end up in more than one of these, and the overlap is significant. A strong control program satisfies many frameworks at once.

## Where compliance leaves you exposed

Here is the uncomfortable part. You can pass every audit in the world and still get breached. Frameworks are black and white — control present or absent, documented or not. Attackers don't operate inside those lines.

A few reasons the gap exists:

**Compliance is point-in-time.** An audit captures a snapshot. The config that was hardened in March drifts by June. A new service goes up in a rush and never makes it into scope. The certificate still hangs on the wall.

**Checklists test for presence, not effectiveness.** "Do you have a firewall?" is a yes/no question. "Is your firewall ruleset actually stopping the thing an attacker would try?" is not on the form. A control can be fully compliant and trivially bypassable.

**Scope creates blind spots.** Frameworks apply to defined systems. The dev box someone spun up, the forgotten subdomain, the vendor integration with broad access — these live outside the audit boundary and are exactly where attackers look first.

**Misconfiguration beats missing controls.** Most real incidents don't come from a control that was absent. They come from one that was present but wrong: over-permissioned access, a default credential never changed, an exposed admin panel, an S3 bucket set to public. Every one of those can sit inside a "passing" environment.

Attackers chain small, boring gaps into a real foothold. None of the individual weaknesses would fail an audit on its own. Together they're a breach.

## Treating compliance as a beginning

The shift is simple to state and harder to live: use the framework as a floor, then go test the building like someone trying to get in.

- **Validate, don't just document.** A control you've never tested under adversarial conditions is an assumption, not a defense.
- **Think in attack paths, not checkboxes.** Ask how someone would actually move through your environment, not whether each line item is marked complete.
- **Close the scope gaps.** The systems outside your audit boundary are still yours when they get popped.
- **Make it continuous.** Drift is constant. Point-in-time assurance ages the moment the auditor leaves.
- **Get an outside perspective.** Penetration testing and red team work exist precisely because the people who built a system can't see its blind spots. That's not a knock on your team — it's how blind spots work.

Compliance tells you that you locked the doors. Only an adversarial test tells you whether the windows are open, the lock picks, and the key is under the mat.

Pass the audit. Then go find what the audit couldn't.
