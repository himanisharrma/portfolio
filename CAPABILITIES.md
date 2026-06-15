# Capabilities → Evidence

Every AI-capability badge on [my profile](https://github.com/himanisharrma) maps to a **committed
artifact you can open** — code, config, or a measured run. No aspirational vocabulary; each row links
to the proof.

## Build & retrieval

| Capability | What it is | Evidence | Proof point |
|---|---|---|---|
| **Claude Code** | Governed agentic-coding (project memory, subagents, hooks, slash commands) | flagship [`CLAUDE.md`](https://github.com/himanisharrma/Identity-Verification-Amazon-Rekognition) | ~230 commits, ~95% AI-co-authored, across 8 months |
| **MCP — I build servers** | A custom MCP server, not just a client | [`mcp-server/index.mjs`](https://github.com/himanisharrma/video-kyc-hackathon/tree/vcip-mcp/mcp-server) | 6 tools + WORM-audit resource; PII masked at the tool boundary; human-gated write |
| **RAG + Evals** | Grounded retrieval + an eval gate run before any prompt ships | [`compliance-qa`](https://github.com/himanisharrma/rekyc-compliance-module/tree/main/compliance-qa) | v1 11/12 → **v2 12/12**; 12-case harness with an out-of-scope refusal trap |
| **Vector Search** | Dense embeddings + BM25 **hybrid** (RRF) | [`vector_retrieve.py`](https://github.com/himanisharrma/rekyc-compliance-module/blob/main/compliance-qa/vector_retrieve.py) | measured BM25 ∩ dense ≈ **62%** of top-6 → hybrid recovers paraphrase misses |
| **LangGraph** | Agent state machine with a self-correction loop | [`graph.py`](https://github.com/himanisharrma/rekyc-compliance-module/blob/main/compliance-qa/graph.py) | `retrieve → generate → verify`, loops on ungrounded; resolved grounded in 1 pass |
| **Tool Use** | Agent tool-loop → structured result | [`KYC-Re-Verification_SabKYC`](https://github.com/himanisharrma/KYC-Re-Verification_SabKYC) `ai-service/` | flagged a real `created_at > approved_at` data quirk in live data |

## Governance & ops

| Capability | What it is | Evidence | Proof point |
|---|---|---|---|
| **LLMOps** | Langfuse tracing of the LLM pipeline | [`observe_eval.py`](https://github.com/himanisharrma/rekyc-compliance-module/blob/main/compliance-qa/observe_eval.py) | 12 traces ingested — retrieve span + generation (tokens/cache) + `eval_pass` score |
| **Guardrails** | Deterministic safety encoded in code | hooks + grounding refusal rule | pre-push secret-scan, doc-drift hooks; refusal rule actively tested by the eval trap |
| **Human-in-the-Loop** | Human approval on every irreversible action | MCP `record_verdict` + maker-checker | only write is human-gated; verifier → risk → approver chain in the KYC platforms |
| **Subagents** | Role-specialized agent pods | [`.claude/agents/`](https://github.com/himanisharrma/video-kyc-hackathon) | code-reviewer, test-writer, security-auditor, aws-cost-auditor |
| **Agent Skills** | A distributable Claude Code plugin | [`finverge-sales-skills`](https://github.com/himanisharrma/finverge-sales-skills) | **8-skill** plugin over a permission-aware dual knowledge base |
| **CI Agents** | AI review/health inside CI | flagship `.github/workflows/` | AI PR review on each PR + a weekly repo-health cron |

## Prompting, context & multimodal

| Capability | What it is | Evidence | Proof point |
|---|---|---|---|
| **Prompt Engineering** | Versioned, eval-tested prompts | [`prompts/system_v1,v2.md`](https://github.com/himanisharrma/rekyc-compliance-module/tree/main/compliance-qa/prompts) | the v1→v2 rules are what moved the eval 11/12 → 12/12 |
| **Prompt Caching** | Stable→volatile request; cached system prefix | [`qa.py`](https://github.com/himanisharrma/rekyc-compliance-module/blob/main/compliance-qa/qa.py) `build_system()` | ~8.7K-token prefix: 1 write, 11 reads (~10× cheaper input) |
| **Context Engineering** | Deliberate context-window design | flagship `CLAUDE.md` memories | multi-month agentic builds via decomposition + handoff protocols |
| **Structured Outputs** | Typed, machine-usable model output | SabKYC summary + the graph `verify` node | JSON verdict the LangGraph routes its retry loop on |
| **Vision + OCR** | Multimodal document + identity verification | flagship / [`video-kyc-hackathon`](https://github.com/himanisharrma/video-kyc-hackathon) | AWS Rekognition (face-match/liveness) + Textract (ID-document OCR) |
| **AWS AI** | Shipped on AWS managed AI services | [flagship](https://github.com/himanisharrma/Identity-Verification-Amazon-Rekognition) | Rekognition + Textract + Comprehend; live face-match proven (same 100% / diff 0%) |

---

*Most of these live in [`rekyc-compliance-module/compliance-qa`](https://github.com/himanisharrma/rekyc-compliance-module/tree/main/compliance-qa) (the RAG / Vector Search / LLMOps / LangGraph builds) and the flagship [`Identity-Verification-Amazon-Rekognition`](https://github.com/himanisharrma/Identity-Verification-Amazon-Rekognition).*
