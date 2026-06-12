# Field Notes — problems I hit building with AI, and what actually worked

> Collected across every project in this portfolio. Format: the problem as I hit it, then
> the practice that survived. Nothing theoretical — each entry cost me real time first.

## 1. UI/UX — from my weakest area to a 95%-hit workflow

**Problem:** I couldn't get good UI out of the AI initially — it threatened every task.
Responsive layouts broke across devices; one base screen rendered differently everywhere.

**What works (my template → design-system → subagents workflow):**
1. Build **one page perfectly** first. Fix it, check it, make it the template.
2. **Extract the design system** from that template (colors, type, spacing, components, states).
3. Have Claude **spawn subagents — one per page/screen** — each building against the design
   system in parallel. This also solves the context-window problem: subagents divide the
   work so no single context gets exhausted.

UI/UX-first has a second payoff: when you fix the UI pillar, everything downstream gets
fixed with it — screen structure, connections, dependencies, features, even the API list.

## 2. Decomposition — the framework everything else depends on

**Versions → Phases → Features → Modules → Sub-modules → Tasks.**
- Every task complete in itself; dependencies and prerequisites mapped; **handoffs mapped**
  (what information must reach the next module).
- Properly decomposed work can be parallelized across subagents safely — and context stays
  effective.
- Refinement I'm testing: **"use case" beats "feature"** as the unit — user-centric, not
  business-centric, and prompts get dramatically more accurate. Granularize to use-case
  level and you get one-shot creations: 10 prompts = 10 features on point.

## 3. Context management — the real enemy is exhaustion

- **300–500 line limit per file, one functionality per file.** End every prompt with a
  modularity check. (Exceptions exist — don't break DB migration files.) Done from the
  beginning, this removes ~90% of the headache.
- **Handoff file** (`handoff_pack.md`): revise it as long conversations drift; before
  compaction, take a screenshot or write a short summary of where you are.
- **Subagents + MCP verification + handoff file together beat compaction**: even after the
  conversation compacts, MCP screenshots show exactly what was actually built — no
  hallucinated state.
- Keep a **docs folder as shared context** (mine came from my note-taking app) that both
  backend and frontend sessions read — a note app can even be wired in as an MCP.
- `/init` + a comprehensive README/CLAUDE.md so the project carries its own context.
- `#` add-to-memory for rules you'd otherwise repeat every session.

## 4. Hallucination combat — default position: it WILL hallucinate

- Claude says "done" on its 7 to-dos one after another; when you check, it isn't. Limiting
  to 4 to-dos didn't fix it. The only reliable workaround I found: **challenge it, every
  time** — "please challenge yourself, please challenge me." It takes 4–5 iterations before
  the confidence is real. This also combats sycophancy (the model agreeing with you).
- **Verify with MCPs, not vibes:** Playwright MCP for what's actually on screen; a DB-viewer
  MCP to see tables and insertions with your own eyes. Build backend with testing first,
  then move to frontend.
- Watch for the deployment-time failure mode: changes applied to the *wrong codebase* while
  the file that needed the change stays untouched — confusion that snowballs into more
  unneeded changes. Plan Mode + agents keep edits pinpointed.

## 5. Architecture first — the two fixed points

- **Database architecture is fundamental.** Normalize from the start; an un-normalized
  design that works at demo scale becomes a system problem at 10-digit-population scale.
- **User flows before code.** Be the product manager *for* Claude: lay the problem out as an
  algorithm, clarify the flow in your own head, write it down — then prompt.
- Backend discipline: **one service/API at a time** — build it, monitor it, test it, verify,
  then move. Never "integrate everywhere at once" (that's how hard-coding and corruption
  creep in during multi-service integration).
- **Centralized configuration** (env, ports, service URLs) resolved a whole class of issues;
  environments separated; deployment should be a single command; **CI/CD in the plan from
  day one** — without it, features keep breaking quietly.

## 6. Models — different models for different tasks

- Sonnet-class models punch above their weight on frontend work; reserve the big model for
  architecture and hard logic.
- **Open-source models are very cheap for narrow tasks** — safe to use once work is
  decomposed into small, isolated pieces (tight context per task = no security concern and
  no convention bleed). The corollary from my flagship: *switching* vendors mid-project on a
  shared codebase without that decomposition destabilizes everything.
- New language/framework versions past the model's training data: have it **research from
  the internet — preferably via official, safe MCPs** rather than free web search (cheaper
  in tokens, more accurate).

## 7. Compliance-domain prompting

- **Right terminology is compression.** "RBI", "PCI-DSS", "GDPR", "DPDP", "security design"
  — each term unpacks a whole rulebook in the model's head. Algorithmic thinking needs the
  right vocabulary.
- Specify the **deployment environment** (platform, instance size) so infrastructure
  suggestions are sized to reality, and keep context tight — IPs, configs, boundaries stated
  explicitly, every time.

## 8. The concepts, in the order I learned them

Nine months compressed: each concept below entered my working vocabulary because a project
forced it, and most have a matching artifact in this portfolio.

- **Prompt engineering as a discipline** — frameworks of instruction, examples, constraints,
  role assignment; meta-prompting (asking AI to write the prompt). Evidence: the prompt
  library and the constitution's structured-answer protocols.
- **Context engineering** — context windows, working in large codebases, why decomposition
  and the 300–500-line rule exist; long-context (1M-token) models changed what "give it the
  whole module" means.
- **Memory systems** — CLAUDE.md project memory, `#` add-to-memory, handoff packs, session
  bootstrap rituals.
- **Tool use / function calling** — an agent is an LLM with tools: search the web, run code,
  query a database, send an email. Evidence: the SabKYC case-summary endpoint's tool loop.
- **MCPs instead of custom integrations** — GitHub MCP, Jira MCP, Playwright MCP, reminder
  and headless tooling, and eventually building my own MCP server (the KYC Orchestrator).
- **RAG** — don't retrain the model on your documents: chunk, retrieve the relevant pieces,
  inject into the prompt, generate. Embeddings vs lexical search. Evidence: compliance-qa
  (BM25 retrieval, cited answers, refusal trap).
- **Agentic workflows** — multi-step autonomous chains (research competitors → build the
  spreadsheet → draft the email report) and parallel subagents (backend / frontend / testing
  specialists; PR-creating agents).
- **Skills** — packaged expertise the agent applies at the right moment: product-strategy
  and PRD-type skills I used, plus custom skills I built (the 9-skill sales plugin, the
  vcip-kyc domain skill).
- **Guardrails** — deterministic hooks (secret scans, doc-drift detection) instead of hoping
  the model behaves; evals to measure prompts before shipping them.
- **Multimodal** — pasting error screenshots and UI mocks into the chat; vision OCR;
  generating presentations and images for product collateral; experimenting with image,
  video, and audio generation models.
- **Model routing** — Sonnet-class for frontend, Opus-class for architecture, cheap/open
  models for narrow decomposed tasks; Gemini/AI Studio and Copilot in the rotation at
  various points.

## 9. Honest roadblocks (still open)

- **DevOps remains a minefield for me** — pipelines ran n times while I figured out
  deployment; it needs its own dedicated learning block.
- **Scope creep** is the tax on AI speed: building is so easy that scope grows, and
  corrective surgery sometimes cuts backend but not frontend (or vice versa). Boundaries in
  the plan, and challenge-everything reviews, are the only brakes I've found.
