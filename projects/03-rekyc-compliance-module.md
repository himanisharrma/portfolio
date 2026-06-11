# Re-KYC Compliance Module

> **The periodic re-verification engine RBI requires, extracted as a clean, portfolio-grade
> module:** FSM-driven case lifecycle, RBAC, compliance crons (PRA/GST checks), bulk triggers,
> mock API, e2e specs — plus a grounded, eval-measured **RAG compliance Q&A** over the Master
> Direction itself.

**Repo:** [`rekyc-compliance-module`](https://github.com/himanisharrma/rekyc-compliance-module) ·
74 curated files (React frontend module · Express rekyc-api · Python+TS backend) ·
README defends 7 design decisions

## What it is

RBI's Master Direction requires periodic KYC re-verification — every 2 years for high-risk
customers, 8 for medium, 10 for low. This module is that obligation as software: identify who's
due, trigger and track re-verification cases through a finite-state machine, enforce role
boundaries (RBAC), run scheduled compliance checks (cron), and keep an auditable trail —
the merchant-facing flow plus the ops machinery behind it.

It was extracted from a larger onboarding platform with **verified test parity**: the pytest
suite produces results identical to the source baseline (37 pass / 12 pre-existing fails) —
proof the extraction changed packaging, not behavior.

## The AI build-out: `compliance-qa/` — grounded, measured, optimized

A RAG pipeline over the **public RBI KYC Master Direction** that a compliance officer can
actually trust:

- **Grounded (RAG):** 188 heading-aware chunks → dependency-free Okapi BM25 → Claude answers
  with excerpt citations and a hard refusal rule for off-corpus questions.
- **Measured (evals):** versioned prompts + a 12-case harness including an out-of-scope trap.
  Result on `claude-opus-4-8`: baseline prompt **11/12** — it confidently answered a GST
  question from general knowledge; shipped prompt **12/12** — the grounding rule closed
  exactly that failure. Run logs committed (`evals/results_v1.json`, `results_v2.json`).
- **Optimized (prompt caching):** stable system prefix (versioned prompt + corpus digest,
  ~8.7K tokens) behind a `cache_control` breakpoint — one cache write, then every request
  reads it at ~0.1× input price. The eval harness prints the cache economics per request,
  and encodes the measured ops constraints (rate-limit and connection retries).

## PM decisions I'd defend in a room

1. **Extraction over exposure** — the original platform repos held company data; the portfolio
   value was *my* re-KYC contribution. Curate 74 files, scrub, verify parity, publish clean.
2. **RAG over fine-tuning** — the regulation is amended repeatedly; re-ingest beats retrain,
   and cited excerpts make every answer auditable by the human who owns the decision.
3. **Evals before shipping** — the v1→v2 delta (hallucination → refusal) is the concrete
   argument for versioned, measured prompts; it's one line of prompt and the whole product.

## AI capabilities demonstrated

**RAG pipeline** (chunking, BM25, cited generation) · **Evals** (versioned prompts, automated
scoring, refusal trap) · **Prompt caching** (stable-prefix design, measured economics) ·
agentic extraction workflow with verified test parity.
