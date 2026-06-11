# The AI Toolkit — how I work as a Tech AI PM

Capability names follow Anthropic's official courses (Anthropic Academy: *Claude Code in Action*,
*Building with the Claude API*, *Claude for Work* track) with OpenAI equivalents noted. Three honest
tiers — every Tier-1 line links to a committed artifact.

---

## Tier 1 — Applied in projects (clickable evidence)

| Capability | Where I used it | Evidence |
|---|---|---|
| **Agentic coding loop** (gather context → act → verify) | Flagship VCIP platform: 141K LOC, 3,045 tests, solo in 9 weeks; 213 of 223 commits AI-co-authored across Claude Opus 4.5→4.8 | `Identity-Verification-Amazon-Rekognition` git log; `docs/portfolio/BY-THE-NUMBERS.md` |
| **CLAUDE.md project memory** | A 1,584-line hardened "AI governance constitution": anti-hallucination rules (prove assumptions with file path + quoted snippet), TDD-first enforcement, ≤2-file edit limits, mandatory RBI compliance gates | Flagship `CLAUDE.md`; hackathon repo `CLAUDE.md` (hardened system prompt + handoff protocol) |
| **Custom MCP server** (tools, resources, prompts) | Built the **"KYC Orchestrator"**: 6 tools, a WORM-audit-trail resource, an orchestration prompt — with client-side PII masking and a 3-layer human-in-the-loop gate on the only irreversible write | `video-kyc-hackathon` → `mcp-server/index.mjs` + README |
| **MCP servers (consuming)** | Playwright (autonomous browser verification), filesystem, GitHub wired into projects | `.mcp.json` in `video-kyc-hackathon`, `cob-rekyc-v2` |
| **Custom subagents** | Role-specialized agent teams: code-reviewer, test-writer, security-auditor, aws-cost-auditor (VCIP); backend-architect, api-documenter, ui-ux-designer, frontend-developer (onboarding platform) | `video-kyc-hackathon` `.claude/agents/`; cob-rekyc-v2 `.claude/agents/` |
| **Agent Skills** | `vcip-kyc` — RBI VCIP domain knowledge packaged as a skill so every session is compliance-aware; plus a **9-skill distributable plugin** (below) | `video-kyc-hackathon` `.claude/skills/vcip-kyc/`; `finverge-sales-skills` |
| **Claude Code plugin (skills at team scale)** | Designed & shipped a 9-skill plugin automating sales collateral (bank/enterprise proposals, product decks, content campaigns) over a governed two-tier public/internal knowledge base | `finverge-sales-skills` — `.claude-plugin/plugin.json`, 9 skill dirs, `kb_loader.py` |
| **Hooks (deterministic guardrails)** | Pre-push secret scanning, doc-drift detection on server edits, session stop-status — policy enforced in code, not promised in prompts | `video-kyc-hackathon` `.claude/hooks/` |
| **Custom slash commands** | /compliance-check (regenerates the RBI compliance matrix), /repo-audit, /secret-scan, /env-doctor, /new-endpoint, /review | `video-kyc-hackathon` `.claude/commands/` |
| **Cross-vendor agent harness (OpenAI Codex)** | The same agents + hooks mirrored for Codex: `.codex/agents/*.toml`, `.codex/hooks.json`, `AGENTS.md` project memory | `video-kyc-hackathon` `.codex/` |
| **Prompt engineering (versioned, reusable)** | A categorized prompt library distilled from building and operating the VCIP platform | `video-kyc-hackathon` `PROMPTS_LIBRARY.md` |
| **Autonomous browser verification (Playwright MCP)** | Agents walking the full KYC journey and documenting it; release E2E checks across 12+ routes with evidence screenshots | Flagship `playwright-screenshots/`, phase-gated `test:phase1–6`; SabKYC E2E screenshot set |
| **Test-driven agentic development** | TDD-first as a constitution rule; 8-phase service-hardening campaign (~560 tests); CI red → green across three release tags | Flagship test suite (3,045 cases), `v0.1.0`→`v0.3.0-ci-all-passing` |
| **AI-assisted security remediation** | Full git-history secret scrub (gitleaks + git-filter-repo across 255 commits); an 11-repo branding/PII remediation program run agentically with quarantine + bundle-backup safety protocol | Flagship Act-3 notes; remediation workspace logs |
| **RAG pipeline (chunking, BM25 retrieval, cited generation)** | Grounded compliance Q&A over the public RBI KYC Master Direction: 188 heading-aware chunks, dependency-free Okapi BM25, answers cite excerpt ids and refuse off-corpus questions | `rekyc-compliance-module/compliance-qa/` |
| **Evals (versioned prompts, measured before shipping)** | 12-case harness with an out-of-scope refusal trap: baseline prompt 11/12 (hallucinated off-corpus), shipped prompt **12/12** — the measured delta is the grounding rule | `compliance-qa/evals/` + `results_v1/v2.json` |
| **Prompt caching** | Stable system prefix (versioned prompt + corpus digest, ~8.7K tokens) behind a `cache_control` breakpoint: 1 write, 11 reads per eval pass at ~0.1× input price; rate-limit-aware harness encodes the measured ops constraints | `compliance-qa/qa.py`, eval logs |

## Tier 2 — Directed at program level

Capabilities I've operated as the orchestrator (the agent executed; I scoped, gated, and verified):

- **Parallel subagent orchestration** — research, evidence-mining, and verification agents run
  concurrently in background during the portfolio/remediation program.
- **Plan Mode / Extended thinking** — plan-first execution for multi-repo, destructive-risk operations
  (every plan reviewed before any edit).
- **Agent architectures** (routing, chaining, verify-loops) — the patterns from Anthropic's *Building
  with the Claude API* course, applied at the workflow level rather than in app code.
- **Context management** — session memory files, handoff protocols, /compact-style hygiene across
  long-running multi-week sessions (the flagship CLAUDE.md §16 "handoff protocol" formalizes this).

## Tier 3 — Currently building with

On the learning path (Anthropic Academy + OpenAI equivalents), with planned first applications:

- **Claude API in-product features** — tool use / function calling + structured JSON output for an
  AI case-summary endpoint (planned: SabKYC).
- **Batch processing** — Message Batches API for the bulk re-KYC summarization path (the
  compliance-qa request shape is batch-ready).
- **Vision / multimodal** — Claude vision field-extraction vs. the existing Textract pipeline
  (a build-vs-buy analysis on the flagship).
- **Headless CI usage** — `claude-code-action` automated PR review on GitHub.
- **Computer use** — agent-driven UI walkthroughs beyond Playwright.

---

### OpenAI / GPT equivalence (the same method, vendor-translated)

Claude Code ↔ **Codex** (see `.codex/` — already configured) · CLAUDE.md ↔ **AGENTS.md** (committed) ·
subagents ↔ **Agents SDK handoffs** · skills/commands ↔ **custom GPTs / Actions** · MCP — now a
**cross-vendor standard** OpenAI has adopted · analysis tool ↔ **Code Interpreter** · Research ↔
**Deep Research** · Artifacts ↔ **Canvas**.

### The operating principle

Anthropic's **AI Fluency** framing (Delegation · Description · Discernment · Diligence) is how I decide
what the agent does versus what I gate: irreversible actions (a KYC verdict, a git push, a deletion)
always carry a human gate — enforced in architecture (see the MCP server's `record_verdict` design),
not in promises.
