# FinVerge Sales Skills — a Claude Code plugin that automates a sales team

> **A PM automating a whole team's output, not a one-off prompt:** nine Agent Skills that turn
> "make a proposal for [bank]" into a finished, branded deck — over a governed two-tier
> knowledge base.

**Repo:** [`finverge-sales-skills`](https://github.com/himanisharrma/finverge-sales-skills) ·
165 files · 42 Python modules · distributable via `.claude-plugin/plugin.json` + marketplace manifest

## What it is

A **Claude Code plugin** packaging a fintech sales team's entire collateral production:

| Skill | Produces |
|---|---|
| `bank-proposal-generator` | Tailored bank proposals (product selection, compliance language, stakeholder framing) |
| `enterprise-proposal-generator` | Enterprise/merchant proposals across 9 verticals with GMV-based pricing tiers |
| `content-campaign` | A 10-week LinkedIn/X content campaign: drafts, audits, a 4-criteria quality filter |
| `post-studio` | Ad-hoc product posts with typographic cards and carousels |
| `pg-product`, `nach-product`, `collect-product`, `orchestrate-product` | Per-product demo decks, one-pagers, FAQs, feature matrices (PPTX/DOCX/XLSX) |

## The architecture decision that matters: the two-tier knowledge base

Sales collateral needs product truth, but product truth includes things you don't put in a
customer deck. The plugin separates **`shared-kb/` (external)** — customer-facing positioning,
features, public comparisons — from an **internal KB layer** loaded separately (`kb_loader.py`).
Skills declare which tier they may read. That's governance designed into the content pipeline,
not reviewed in after the fact.

## Why it's a PM artifact, not just code

- Each skill encodes a **workflow the team actually runs** — trigger phrases, audience framing
  (CFO vs CTO vs Head of Digital), compliance language (RBI/NPCI/PCI-DSS), brand application,
  output format negotiation.
- **Skills are the product surface**: a salesperson types one sentence; the skill handles
  product selection, KB retrieval, deck structure, and brand styling. Multi-hour manual
  process → one command, for the whole team.
- Distribution is first-class: plugin + marketplace manifests, versioned, installable.

## AI capabilities demonstrated

**Agent Skills at team scale** (a 9-skill distributable Claude Code plugin — Anthropic's
"Introduction to agent skills" capability, taken to production shape) · knowledge-base
architecture with progressive disclosure · document generation pipelines (PPTX/DOCX/XLSX).
