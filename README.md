# Health & Care AI Engineering Second Brain

My 18-month Health & Care AI Engineer Second Brain: a connected knowledge base that turns learning and project experience into reusable engineering judgement and portfolio evidence.

## Purpose

**Capture → Connect → Critique → Compress → Reuse**

- **Capture** what I learn, build, test and discover, including failures and evidence.
- **Connect** lessons across learning, NHS domain knowledge, engineering projects, governance, research and interview evidence.
- **Critique** assumptions, limitations, risks and gaps in validation.
- **Compress** detailed work into clear principles, decisions, interview stories and next experiments.
- **Reuse** those insights in future architecture, implementation, evaluation and professional development.

## Engineering progression

The roadmap connects five stages of an evolving operational intelligence system:

1. **NHS ICB OPEL Predictor** — predictive insight into operational pressure.
2. **NHS Operational Data Platform** — validated data, lineage and reliable analytical foundations.
3. **Healthcare Document Intelligence / RAG** — governed retrieval of operational guidance and evidence.
4. **Agentic Operational Assistant** — controlled tool use supported by evidence, verification and human oversight.
5. **NHS Sovereign Operational Intelligence & Evidence Copilot** — the longer-term integration of operational data, prediction, authoritative evidence and auditable assistance.

These stages describe the intended progression; they do not imply that every system is complete or deployed.

## Repository guide

| Location | Purpose |
| --- | --- |
| [CURRENT_STATUS.md](CURRENT_STATUS.md) | Current stage, completed work, findings, limitations and next direction |
| [learning/](learning/) | Technical learning and reusable study notes |
| [projects/](projects/) | Engineering project records, experiments and cross-project connections |
| [nhs/](nhs/) | NHS operational context and domain knowledge |
| [governance/](governance/) | Safety, evidence authority, accountability and evaluation principles |
| [research/](research/) | Research questions and connections to future system design |
| [interview_evidence/](interview_evidence/) | Reusable evidence of engineering decisions, outcomes and judgement |
| [weekly_reviews/](weekly_reviews/) | Captures, critiques, compressed reviews and the weekly template |

Folders awaiting their first notes contain a `.gitkeep` placeholder so the structure is retained in Git.

## Current progress

- **Week 22 — COMPLETE:** the recorded governed evidence workflow builds on Architecture v2 with structured, provenance-verified, lifecycle-aware, precedence-aware and manager-readable evidence. Detailed Week 22 validation results and source references still need to be captured in this Second Brain.
- **Week 21 — COMPLETE:** Architecture v2 was promoted after the controlled synthetic v1-v2 comparison. V2 recorded **82.22% Top-1, 82.22% Top-k, 100% abstention accuracy and 100% Active-only evidence**; two retrieval wins, no losses and no unsafe AUTO_ANSWER outcomes on the reported abstention/lifecycle checks. The latest detailed regression record here is **541 passed in Week 21**, not a newly verified Week 22 count.
- **Week 23 — NEXT:** the next roadmap stage, preserving the recorded Week 22 evidence-assurance baseline. A detailed implementation plan is not yet recorded here.
- **Working architecture:** initial Hybrid retrieval → evidence sufficiency → deterministic router → at most one bounded recovery route → final evidence sufficiency → retrieval/governance bridge → existing answer and citation governance. Retrieval success does not itself permit an answer; downstream PASS cannot override an earlier ABSTAIN or REVIEW_REQUIRED.
- See [CURRENT_STATUS.md](CURRENT_STATUS.md) for the detailed Week 21 results, Week 22 status, continuity gaps and preserved history. These are controlled synthetic prototype results, not production NHS performance.

### Retained Week 19–20 milestones

- **Week 19 — COMPLETE:** grounded answer governance, citation verification, high-risk claim protection, guarded semantic rescue, evidence-set relationships and corrective false-premise validation. Reported regression at that milestone: **338 passed**.
- **Week 20 Days 1–2 — COMPLETE:** frontier-model/agent and retrieval reviews established the direction “Simplify the intelligence layer, preserve the assurance layer.” Keep the hybrid foundation; evaluate bounded tools, reranking, iterative retrieval and relationship-aware expansion. Long context complements RAG; full GraphRAG is not adopted now. Data Formulator is a pilot/design-borrowing candidate; SQL, PostgreSQL and Power BI remain.
- **Week 20 — COMPLETE through Day 6:** “Simple intelligence, strong assurance.” Architecture v1 was the tested baseline and Architecture v2 was proposed at that milestone; Week 21 subsequently promoted v2. Fabric / OneLake remains a future enterprise data direction, Foundry a managed AI runtime candidate, and Entra / managed identity / RBAC / private networking the deployment direction, not claims of completed migrations.
- **Principles retained:** model risk and change control, pre-decision safety, control tower / exception management and recovery learning. Detect → Prioritise → Explain → Verify → Human Decide → Learn. Build deployment evidence alongside the product; automate checks, not accountability.

## Week 19 Day 1 — Historical Capture

The first Second Brain cycle captures and connects the Weeks 17–18 Healthcare Document Intelligence work:

- [Healthcare Document Intelligence project record](projects/healthcare_document_intelligence.md)
- [Cross-project connections](projects/cross_project_connections.md)
- [Agentic design connections](research/agentic_design_connections.md)
- [Week 19 Day 1 capture](weekly_reviews/week19_day1_capture.md)
- [Week 19 Day 1 review](weekly_reviews/week19_day1_review.md)

Key themes include evidence sufficiency, document authority, selective human review, measurable governance and testing whether added complexity improves results. At that milestone, the next experiment was to expand the evidence-quality benchmark from 14 to approximately 30–50 controlled cases. The subsequent Week 19 retrieval benchmark reached 75 cases; see the current status above.

Reported results come from a small synthetic benchmark with prototype controls; they are not production or clinical validation. See the linked project record and review for the supporting context and limitations.

## Working rhythm

Start with [current status](CURRENT_STATUS.md), capture the week's evidence, connect it to the wider roadmap, and use the [weekly review template](weekly_reviews/TEMPLATE.md) to critique and compress the work. Reuse the resulting principles and interview evidence in subsequent projects and update the status as work progresses.

This repository holds the Second Brain knowledge base. The Healthcare Document Intelligence / RAG implementation is maintained in its separate repository.
