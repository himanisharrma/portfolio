# Re-KYC Sprint Prototype

> **Sprint-one product thinking, shipped as a clickable artifact:** an RBI-aligned Re-KYC
> journey for payment-aggregator merchants — dashboard banner → status stepper → six-step
> guided KYC update wizard — scoped deliberately as a front-end slice to validate the journey
> before any backend investment.

**Repo:** [`re-kyc-sprint-prototype`](https://github.com/himanisharrma/re-kyc-sprint-prototype) ·
44 files · React/Vite, sanitized demo data · README includes demo GIF + screenshots and links
the in-app banner to the actual RBI Master Direction

## The product case

RBI's Master Direction makes KYC periodic, not one-time. For a platform with a large merchant
base, the cost of failure is concrete: merchants miss Re-KYC deadlines → payment acceptance
limits or freezes → support load and churn. The prototype attacks the *experience* problem —
detect who's due, nudge in time, make the update low-friction — because that's where
compliance programs actually lose merchants.

**The scoping decision is the point:** sprint one validates reminder → form → upload → submit
with stakeholders using a clickable UI and demo-state controls, before paying for backend,
review tooling, or integrations. (That backend investment exists today as
[`rekyc-compliance-module`](03-rekyc-compliance-module.md) — the prototype is where the
journey was de-risked.)

## What's in it

Merchant dashboard with a dynamic "Re-KYC Pending" banner and status stepper · six-step KYC
update wizard (pre-filled sanitized data, document upload, address-change validation) · demo
controls to switch compliance states live in a stakeholder review.

## AI capabilities demonstrated

Built 4/4 AI-co-authored (Claude Opus 4.7/4.8 trailers) — and unusually, **the AI-PM working
method ships with the code**: `AI_PM_NOTES.md` (how the PM directed the agentic build) and
`DEMO_SCRIPT.md` (the stakeholder walkthrough) are committed as first-class docs. The repo is
a small, honest record of what one sprint of AI-assisted product work looks like.
