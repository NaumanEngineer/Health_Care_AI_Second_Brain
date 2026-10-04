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

- **Week 19 — COMPLETE:** grounded answer governance, citation verification, high-risk claim protection, guarded semantic rescue, and evidence-set relationship / corrective false-premise validation. Final reported full regression: **338 passed**.
- **Week 20 Day 1 — COMPLETE:** Frontier Models and Agent Architecture Review. “Simplify the intelligence layer, preserve the assurance layer.” Week 19 Architecture v1 remains the tested baseline; 338 tests last passed, with no rerun for the documentation-only Day 1 commit.
- **Week 20 Day 2 — COMPLETE:** RAG, Retrieval and Evidence Architecture Review. Keep the hybrid foundation and Hybrid Rescue for now; evaluate reranking, bounded iterative retrieval and relationship-aware expansion. Long context complements RAG; full GraphRAG is not adopted now. Data Formulator is a pilot / design-borrowing candidate, while SQL, PostgreSQL and Power BI remain. Architecture v2 is a proposal; the tested v1 baseline and 338-test result are unchanged.
- **Week 20 — COMPLETE through Day 6:** Technology & Architecture Refresh Gate. “Simple intelligence, strong assurance.” Architecture v1 remains the tested evidence-governed RAG baseline; the latest reported full regression remains **338 passed**, with no new test run for this documentation update.
- **Final direction:** one strong orchestrator + bounded tools; the hybrid retrieval foundation with proposed reranking, bounded agentic retrieval, relationship-aware expansion and selective long context; deterministic assurance and human accountability preserved. Fabric / OneLake is a future enterprise data path, Foundry a future managed AI runtime candidate, and Entra / managed identity / RBAC / private networking the deployment direction. These are plans, not completed migrations.
- **Governance and operating model:** model risk and change control, pre-decision safety, control tower / exception management and recovery learning. Detect → Prioritise → Explain → Verify → Human Decide → Learn. Build deployment evidence alongside the product; automate checks, not accountability.
- **Week 21 — NEXT:** reranker evaluation; bounded agentic retrieval; relationship-aware retrieval; a clean orchestrator; Architecture v2 integration tests; and an Architecture v1 vs v2 benchmark. **Does Architecture v2 retrieve better evidence than Architecture v1 without increasing unsafe behaviour?** Architecture v2 remains unvalidated.
- See [CURRENT_STATUS.md](CURRENT_STATUS.md) for final benchmark results, architecture, limitations and retained milestone history.

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
