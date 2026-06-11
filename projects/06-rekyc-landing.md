# Re-KYC Platform with Landing Page

> **The full commercial loop in one repo:** public marketing page → merchant self-service
> onboarding → Verifier → Risk Assessor → Approver pipeline → admin console with single and
> bulk (Excel/CSV) Re-KYC triggers — real-time dashboards throughout.

**Repo:** [`re-kyc-with-landing-page`](https://github.com/himanisharrma/re-kyc-with-landing-page) ·
178 files · React/TS (Vite) + Express + Socket.io · repo README has the architecture diagram,
role-by-role feature map, API summary, and the KYC workflow state machine

## What it is

A working reference implementation of an end-to-end KYC platform, deliberately including the
parts demos usually skip:

- **The funnel, not just the form** — a public landing page feeding merchant signup, because
  KYC software is also acquisition software.
- **Human-in-the-loop pipeline** — three distinct reviewer roles with separate queues and
  permissions (Verifier → Risk Assessor → Approver), matching how regulated ops teams
  actually segregate duties.
- **Re-KYC at operational scale** — single-merchant triggers for exceptions, **bulk
  Excel/CSV-driven triggers** for the periodic sweep, configurable rules, automatic due-date
  computation, and a real-time status banner on the merchant side.
- **Audit log on every action** — the compliance requirement treated as a first-class feature.
- **Real-time everywhere** — Socket.io pushes state changes to every affected dashboard.

## AI capabilities demonstrated

**Agentic coding loop end-to-end** — 6/6 commits AI-co-authored (Claude Opus 4.7 trailers);
the build was also *repaired* in the loop (a missing `react-is` dependency had broken dev and
build — found and fixed during the agentic session, then verified by running both).

## Honest scope notes

Demo-grade seeds and credentials ship in the repo for reviewability; pre-existing TypeScript
strictness errors remain flagged (Vite dev/build are green). The point of the repo is the
workflow architecture and role UX, not production hardening.
