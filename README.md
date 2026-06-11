# Himani Sharma — Tech AI Product Manager · Portfolio

**Fintech / KYC-compliance product manager who ships.** I build regulated-domain products (Video KYC,
Re-KYC, onboarding) end-to-end — product strategy, architecture, code, tests, AWS infra — using a
governed AI engineering system I design and operate myself: Claude Code with project-memory
constitutions, custom subagents, skills, hooks, slash commands, and a custom MCP server; the same
harness mirrored on OpenAI Codex.

> Every AI-capability claim in this portfolio links to a committed artifact you can open — a config, a
> server, a test run, a screenshot. Nothing here is aspirational vocabulary.

---

## Flagship

### 🎥 [VCIP Platform — RBI-Compliant Video KYC](projects/01-vcip-platform.md)
**141K LOC · 3,045 tests · solo, 9 weeks.** Production-grade Video Customer Identification: AWS
Rekognition liveness & face-match, live WebRTC agent calls, 19-state Maker-Checker workflow, RBI
compliance engineering — built inside a 1,584-line AI governance constitution.
→ repo: [`Identity-Verification-Amazon-Rekognition`](https://github.com/himanisharrma/Identity-Verification-Amazon-Rekognition) (branch `portfolio`)

## Projects

| Project | One-liner | AI story |
|---|---|---|
| [VCIP MCP Server — "KYC Orchestrator"](projects/02-vcip-mcp-server.md) | A 6-tool MCP server that lets an AI agent run an assisted KYC review — with PII masking and a human-gated verdict | **Built a custom MCP server**; subagents, skills, hooks, slash commands in the same repo — mirrored for Claude *and* Codex |
| [Re-KYC Compliance Module](projects/03-rekyc-compliance-module.md) | Periodic re-verification engine: FSM, RBAC, compliance crons, bulk triggers — extracted clean with verified test parity | Governed agentic extraction; 7 defended design decisions |
| [Sales Skills Plugin](projects/04-sales-skills-plugin.md) | A 9-skill Claude Code plugin automating a sales team's proposals, decks & campaigns over a two-tier knowledge base | **Shipped a distributable Claude Code plugin** — a PM automating a whole team's workflow |
| [SabKYC — KYC Re-Verification](projects/05-sabkyc.md) | Multi-role KYC re-verification portal (admin / verifier / risk / approver / merchant) | MCP-driven Playwright E2E verification with evidence screenshots |
| [Re-KYC Platform with Landing Page](projects/06-rekyc-landing.md) | Full-stack KYC management: Verifier → Risk → Approver workflow, bulk Excel-driven Re-KYC | 100% AI-co-authored build in the agentic loop |
| [Re-KYC Sprint Prototype](projects/07-sprint-prototype.md) | RBI-aligned periodic-KYC-refresh prototype, sprint-scoped | Ships its own `AI_PM_NOTES.md` + `DEMO_SCRIPT.md` |

*(Project pages are being added top-down; table links activate as pages land.)*

## How I work with AI

**[→ The AI Toolkit](AI_TOOLKIT.md)** — every capability I use, in the vocabulary of Anthropic's
official courses (Anthropic Academy / Skilljar) and their OpenAI equivalents, in three honest tiers:
**applied in projects** (with linked evidence) · **directed at program level** · **currently building with**.

The short version:

- **Agentic coding at scale** — the flagship is 95% AI-co-authored (213/223 commits) across three Claude
  model generations, governed by a hardened CLAUDE.md project memory I authored.
- **The full Claude Code surface** — custom **subagents** (code-reviewer, test-writer, security-auditor,
  aws-cost-auditor), **Agent Skills** (`vcip-kyc` domain skill), **hooks** (pre-push secret scan,
  doc-drift detection), **slash commands** (/compliance-check, /repo-audit, …), **MCP servers**
  (Playwright, filesystem, GitHub, and one I built).
- **Cross-vendor** — the same agent harness configured for OpenAI Codex (`.codex/` agents + hooks,
  `AGENTS.md`), because the method matters more than the vendor.
- **Verification culture** — phase-gated E2E suites, autonomous Playwright-MCP browser walkthroughs,
  evidence screenshots, "every number with its evidence" docs.

## Domain

RBI Master Direction KYC · V-CIP (Video customer identification) · periodic Re-KYC · Maker-Checker
segregation · Aadhaar masking & consent · WORM audit trails · payment-aggregator merchant onboarding.

---

*This is a private, invite-only portfolio. Code references link to private repos — access on request.*
