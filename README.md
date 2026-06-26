# Himani Sharma — Payments & Fintech PM

Payments and fintech product manager. Consumer-fintech roots at Paytm (UPI, lending, co-branded cards);
product ownership at a payments aggregator, where I shipped the platform's first merchant re-verification
flow end to end. I also build with AI, so the products I design, I can ship myself.

🌐 **Live portfolio →** [himanisharrma.vercel.app](https://himanisharrma.vercel.app)

> Every project here links to a committed artifact you can open — a config, a server, a test run, a
> screenshot. Nothing is aspirational vocabulary.

---

## What I do

- 💳 **Payments & Fintech** (consumer & B2B) — UPI & payments, lending & cards, collections & payouts
- 🛠️ **Builds with AI** — I use AI to turn product ideas into working software I can test and ship
- 📈 **Commercial & Growth** — market research, GTM, pricing & positioning (the 3.0 payments launch)
- 🔁 **Reconciliation & Settlement** — PayOps, a self-built control room: match, net-settle, exception states

## Experience

- **Product Associate · SabPaisa** (payments aggregator, 2025–now) — product delivery, GTM and
  partner-bank pitches for the **3.0 payments launch** (~6–9 products across payment gateway, no-code
  collections, onboarding, settlement, orchestration and POS). Shipped the
  platform's first merchant **re-verification** flow, frontend and backend, live to **~135 merchants**
  and cutting re-verification turnaround **from weeks to days**, with a **configurable risk trigger** so
  policy can change without an engineering cycle.
- **Product Associate (freelance) · YourGold** (2025) — integrated Cashfree's UPI gateway for live gold
  buy/sell and **payout** flows: onboarding, verification and error-recovery for reliable disbursements.
- **Product Operations Associate · Paytm** (2021–24) — 10+ products (Postpaid, Personal Loans,
  co-branded Cards); key role in the **UPI rollout** (P2M online & offline, and P2P). Data-driven
  enhancements lifting **productivity ~93%** and **quality ~96%**. R&R award.

## Selected work

*Payments products, built end-to-end. Feature highlights, not line counts.*

| Project | What it is | Highlights |
|---|---|---|
| [PayOps Copilot](https://github.com/himanisharrma/payops-copilot) | Reconciliation & settlement control room — matches orders, gateway exports and bank settlements, nets settlement after fees & GST, sorts every order into six states | 88 tests · 18 migrations · AI-bounded |
| [Identity Verification Platform](projects/01-vcip-platform.md) | Video identity verification for merchant onboarding — liveness, face-match, maker-checker, full audit trail | Live face-match · agent review · approver flow |
| [Customer Onboarding Portal](projects/06-rekyc-landing.md) | Full-stack merchant onboarding & re-verification — multi-role workflow, configurable triggers | 5-role workflow · trigger-config · React + Node |
| [Compliance Intelligence](projects/03-rekyc-compliance-module.md) | Grounded Q&A over the RBI KYC rules — hybrid retrieval, cited answers, eval-gated | Hybrid retrieval · 12-case eval · cited answers |
| [FinVerge Sales Skills](projects/04-sales-skills-plugin.md) | A Claude Code plugin automating GTM collateral over a permission-aware knowledge base | 8 skills · permission-aware KB · GTM tooling |
| [Agentic Verification (MCP)](projects/02-vcip-mcp-server.md) | A 6-tool MCP server for assisted verification — safety gates, PII-masked at the boundary | 6 tools · safety gates · PII-masked |

*More: [KYC Re-Verification Portal](projects/05-sabkyc.md) · [Re-KYC Sprint Prototype](projects/07-sprint-prototype.md)*

## Recent depth

My most recent role went deep on the regulated edge of merchant onboarding: RBI KYC Master Direction,
V-CIP (video identity), periodic re-verification, maker-checker segregation, Aadhaar masking & consent,
and WORM audit trails — the hardest part of getting a merchant safely onto a payments platform.

## How I build with AI

I build with AI, with a clear rule: **AI assists · rules decide · humans approve · logs prove.**

- **[→ Capabilities & Evidence](CAPABILITIES.md)** — every capability mapped to the exact repo/file that proves it, with a measured proof point.
- **[→ The AI Toolkit](AI_TOOLKIT.md)** — every capability I use, in three honest tiers: applied in projects (with linked evidence) · directed at program level · currently building with.
- **[→ Field Notes](FIELD-NOTES.md)** — the problems I hit building with AI and the practices that survived.

The short version:

- **Agentic coding at scale** — the identity-verification platform is ~95% AI-co-authored across three
  Claude model generations, governed by a hardened CLAUDE.md project memory I authored.
- **The full Claude Code surface** — custom subagents (code-reviewer, test-writer, security-auditor),
  Agent Skills, hooks (pre-push secret scan, doc-drift), slash commands, and MCP servers, including one I built.
- **Cross-vendor** — the same agent harness configured for OpenAI Codex, because the method matters more than the vendor.
- **Verification culture** — phase-gated E2E suites, autonomous Playwright browser walkthroughs, evidence screenshots.

---

*Every reference links to a public repo or file you can open directly.*
