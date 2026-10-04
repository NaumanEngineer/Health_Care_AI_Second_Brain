# Current Status



## Training Stage



- Roadmap: 18-Month Health & Care AI Engineer

- Current Week: Week 20 — Technology & Architecture Refresh Gate — COMPLETE (Day 6 closeout)

- Week 19: COMPLETE

- Week 20 Day 1: COMPLETE

- Week 20 Day 2: COMPLETE

- Next: Week 21 — Architecture v2 implementation and comparative evaluation

- Current Focus: Week 20 refresh gate complete; prepare the Week 21 build while preserving the tested Architecture v1 baseline

- Study Model: Learn → Build → Test → Govern → Document → Reuse



---



# Current Flagship Progression



1. NHS ICB OPEL Level Predictor

2. NHS Operational Data Platform

3. Healthcare Document Intelligence / RAG Assistant

4. Agentic Operational Assistant

5. NHS Sovereign Operational Intelligence & Evidence Copilot



The objective is to evolve these systems into one coherent NHS operational intelligence and evidence platform rather than build disconnected projects.



---



# Current Flagship



## Healthcare Document Intelligence / Governed RAG Assistant



Earlier Week 19 ingestion and retrieval architecture (historical; final governed architecture below):



Documents  

→ extraction  

→ cleaning  

→ chunking  

→ metadata  

→ embeddings  

→ semantic retrieval  

→ BM25 retrieval  

→ hybrid retrieval  

→ query scope gate  

→ evidence sufficiency  

→ targeted retrieval rescue  

→ lifecycle-safe evidence  

→ human review decision  

→ grounded answer / abstention



---



# Most Recently Completed Work



## Week 20 Day 6 — COMPLETE: Technology & Architecture Refresh Gate Closeout

**Progress:** Week 19 = COMPLETE; Week 20 = COMPLETE; Week 21 = NEXT.

This closeout records the project owner's supplied Week 20 decisions. It consolidates the architecture direction; it does not claim that Architecture v2 has been implemented or validated. Earlier Day 1 and Day 2 records remain below as history.

### Baseline and core principle

**Architecture v1 remains the tested evidence-governed RAG assurance baseline.** The latest reported full regression baseline remains **338 tests passed**. This documentation-only closeout does not represent a new test run.

The controlled synthetic Hybrid Rescue benchmark remains **82.22% Top-1, 82.22% Top-k, 100% abstention accuracy and 100% Active-document compliance**. These are prototype benchmark results, not production NHS performance.

> Simple intelligence, strong assurance.
>
> Simplify the intelligence layer, preserve the assurance layer.

### Final architecture direction

- Use one strong orchestrator with bounded tools; reduce unnecessary specialist-agent chains and custom orchestration.
- Keep the hybrid retrieval foundation. Evaluate dedicated reranking, bounded agentic / iterative retrieval, relationship-aware retrieval and selective long-context reasoning. Keep Hybrid Rescue for now pending comparative evidence.
- Preserve deterministic assurance: evidence sufficiency, lifecycle/version checks, citation verification, high-risk claim protection, evidence-set reasoning and corrective false-premise handling.
- Retain human accountability, auditability and `AUTO_ANSWER / REVIEW_REQUIRED / ABSTAIN`. A more capable intelligence model must still pass evaluation before replacing the current model.
- Treat Fabric / OneLake as the future enterprise data path and Microsoft Foundry as a future managed AI runtime candidate. Keep PostgreSQL and Power BI; industrialize selectively rather than migrating by default.
- Plan deployment around Entra ID, managed identity, RBAC, least privilege, private networking and auditable access. These are target controls, not claims of a completed deployment.

> Prototype locally. Industrialize selectively. Keep ownership of the NHS-specific assurance layer.

### Governance and deployment readiness

The intended purpose remains operational decision support with human accountability, not autonomous high-risk clinical or operational action. Carry forward DCB0129 / DCB0160-minded hazard logging, DPIA / privacy review, data minimisation, development/production separation, version/change control, regulatory readiness, DTAC-style readiness and procurement evidence. Deployment-readiness gaps still need explicit assessment; this review is not a compliance certification.

> Build deployment evidence alongside the product rather than bolting governance on at the end.

### High-reliability lessons to carry forward

| Capability | Design lesson |
| --- | --- |
| Operational Control Tower | Detect meaningful exceptions, explain likely drivers, consider dependencies and track trends. |
| Exception / Severity Triage | Use Detect → Triage → Contain → Recover → Learn, with severity and evidence confidence made visible. |
| Pre-Decision Safety Checklist | Automate checks, expose readiness and provide an explicit challenge mechanism; preserve human accountability. |
| AI Model Risk & Change Register | Record usage limits, independent validation, controlled changes and periodic reviews. |
| Recovery / Lessons-Learned Loop | Track recovery indicators and turn incidents and failed experiments into reusable learning. |

> Automate the checks, not the accountability.

**Emerging USP:** A governed NHS operational control tower that detects meaningful exceptions, explains likely drivers, retrieves relevant policy evidence, verifies the safety of the briefing, and directs management attention to cases that genuinely require human judgement.

**Operating model:** Detect → Prioritise → Explain → Verify → Human Decide → Learn.

### Week 21 — must build and evaluate next

1. Reranker evaluation.
2. Bounded agentic retrieval.
3. Relationship-aware retrieval.
4. A clean orchestrator with bounded tools.
5. Architecture v2 integration tests.
6. Architecture v1 vs v2 benchmark.

**Central question:** Does Architecture v2 retrieve better evidence than Architecture v1 without increasing unsafe behaviour?

Keep the Architecture v1 baseline and benchmark evidence intact. Evaluate the proposed improvements before promotion; no Architecture v2 performance claim is established by this closeout.

---

## Week 20 Day 2 — COMPLETE: RAG, Retrieval and Evidence Architecture Review

**Status recorded:** 29 September 2026, using the verified review supplied by the project owner.  
**Progress at Day 2 completion:** Week 19 and Week 20 Days 1–2 were complete; Day 3 was next. See the Week 20 closeout above for current progress.

### Tested Architecture v1 baseline

The Day 2 retrieval-stack view is:

```text
Question
→ Semantic Retrieval
+ BM25 Keyword Retrieval
→ Hybrid / RRF
→ Hybrid Rescue
→ Active-Document Filtering
→ Evidence Sufficiency
→ Answer Generation
→ Citation / Governance Checks
```

This is a retrieval-focused conceptual view, not a claim that the existing scope gate or pre-generation governance has been removed or that implementation ordering changed. The full Week 19 governed architecture remains preserved below.

| Controlled synthetic Hybrid Rescue benchmark | Result |
| --- | ---: |
| Top-1 accuracy | 82.22% |
| Top-k accuracy | 82.22% |
| Abstention accuracy | 100% |
| Active-document compliance | 100% |

These are controlled synthetic benchmark results, not production NHS performance. The latest verified full regression baseline remains **338 tests passed**; this documentation update does not represent a new test run.

### Day 2 decisions

| Decision | Components |
| --- | --- |
| KEEP | Semantic retrieval; BM25 / keyword retrieval; hybrid retrieval / RRF; lifecycle filtering; evidence sufficiency; SQL; PostgreSQL; Power BI |
| KEEP FOR NOW | Hybrid Rescue |
| UPGRADE CANDIDATES | Dedicated reranking; lightweight relationship metadata; selective long-context reasoning |
| STRONG UPGRADE CANDIDATES | Bounded agentic / iterative retrieval; relationship-aware retrieval expansion |
| DO NOT ADOPT NOW | Full GraphRAG |
| PILOT / BORROW DESIGN | Microsoft Data Formulator; borrow its Data Threads design pattern |

Hybrid Rescue materially improved the controlled benchmark. Keep it for now, but consider simplifying it later if reranking or iterative retrieval can replace hand-built rescue logic more generally. Upgrade candidates require evaluation; they are not implemented or promoted by this review.

### Long-context principle

> RAG finds the right evidence. Long context reasons across a larger selected evidence set. Governance verifies the resulting answer.

Long context complements RAG. It does not replace lifecycle filtering, provenance, citation verification, evidence sufficiency, human review or abstention.

### Relationship-aware retrieval

Week 19 reasoning supports `CONFLICT`, `COMPLEMENTS`, `REPLACES` and `TAKES_PRECEDENCE`.

Future retrieval enhancement:

```text
Hybrid retrieval
→ Retrieve relevant document
→ Inspect verified document relationships
→ Expand to connected documents
→ Lifecycle filtering
→ Optional reranking
→ Evidence package
```

**Full GraphRAG: DO NOT ADOPT NOW.** Its infrastructure and maintenance complexity is too high for the current value. Prefer borrowing the graph/relationship design pattern without introducing a full graph stack.

### Microsoft Data Formulator — PILOT / BORROW DESIGN

Data Formulator is not a replacement for SQL, PostgreSQL or Power BI, and is not a core production dependency yet. Potential value includes rapid exploratory analysis, conversational structured-data investigation, faster chart creation, branching analytical workflows and reduced time-to-insight.

**Data Threads** offers a potential future pattern:

```text
Main operational question
→ Workforce branch
→ Bed-pressure branch
→ Incident branch
→ External-pressure branch
→ Evidence-backed synthesis
```

The branches represent separate analytical workstreams, not a requirement for a chain of specialist agents.

Pilot questions:

1. Which Trust deteriorated most over the last seven days?
2. Is staffing pressure associated with higher OPEL levels?
3. Which dates combine high A&E breach, bed pressure and incident activity?

Evaluate a future pilot using time to first useful insight, correctness, follow-up flexibility, visual quality, repeatability, auditability, governed metric consistency and analyst time saved. These are proposed evaluation criteria, not measured benefits.

### Governed metric rule

The AI exploration layer may help investigate data but must not redefine governed operational metrics such as **bed occupancy, A&E breach, staffing pressure or OPEL level**.

### Architecture v2 retrieval direction — proposed

```text
Question
→ Intent / Complexity Assessment
→ Hybrid Retrieval
→ Optional Reranking
→ Optional Agentic Retrieval for Complex Questions
→ Relationship-Aware Expansion
→ Lifecycle Filtering
→ Selected Evidence Package
→ Long-Context Reasoning Where Justified
→ Deterministic Assurance
→ AUTO_ANSWER / REVIEW_REQUIRED / ABSTAIN
```

This direction preserves the assurance and human-review responsibilities established in Architecture v1. It is a design proposal, not a replacement validated by the existing benchmark.

### Key Day 2 principle

> Do not replace a strong hybrid retrieval foundation. Add smarter behaviour around it.

### Economic interpretation

Future retrieval evaluation should measure retrieval accuracy, analyst minutes saved, policy-search time saved, manual document lookups avoided, cost per governed query, false acceptance rate and human-review rate.

### Day 3 Plan Recorded at Day 2 Completion

**Microsoft Fabric / Azure / data architecture / deployment review.**

Central question: **Which parts of the project should remain local/open-source, and which should move toward enterprise-grade Microsoft infrastructure?**

---

## Week 20 Day 1 — COMPLETE: Frontier Models and Agent Architecture Review

**Week 20 theme:** Technology & Architecture Refresh Gate.  
**Progress at Day 1 completion:** Week 19 and Week 20 Day 1 were complete; Day 2 was next. See the Day 2 record above for current progress.  
**Baseline:** The Week 19 governed architecture remains the tested **Architecture v1** baseline. Day 1 records a proposed direction, not an implemented architecture replacement.

### Latest verified RAG repository state

The following state is recorded from the project owner's verified update on 28 September 2026. It describes the **Healthcare Document Intelligence / RAG repository**, not this Second Brain repository:

- Git branch: `main`.
- Local = `origin/main`.
- Working tree clean.
- Latest commit: `f37b91f` — Add Week 20 Day 1 frontier model and agent architecture review.
- Week 19 completion commit: `54ebeca` — Complete Week 19 evidence-set reasoning and false-premise governance.
- Latest verified full regression baseline: **338 tests passed**.
- The Week 20 Day 1 commit was documentation-only, so tests were not rerun.

### Core principle

> Simplify the intelligence layer, preserve the assurance layer.

Simplify unnecessary specialist agents, duplicated orchestration, excessive prompt scaffolding and custom runtime infrastructure where managed services can safely replace it.

Preserve evidence sufficiency, lifecycle/version checks, citation verification, high-risk claim checks, evidence-set reasoning, corrective false-premise handling, `AUTO_ANSWER / REVIEW_REQUIRED / ABSTAIN`, human review and auditability.

### Architecture pivot

Move away from many specialist agents, heavy custom orchestration and large prompt scaffolding.

Move toward one strong governed orchestrator, bounded specialist tools, managed runtime where appropriate, controlled retrieval, deterministic assurance and human oversight.

### Agent design principle

| Responsibility | Appropriate role |
| --- | --- |
| Agents | Flexible reasoning, planning, coordination, synthesis and independent parallel analytical workstreams |
| Tools | Retrieval, SQL, calculations, policy lookup, lifecycle validation, evidence validation, citation verification and deterministic governance |
| Governance | Final safety decision, review routing, abstention and auditability |

### Provisional KEEP / UPGRADE / REPLACE / IGNORE decisions

| Decision | Components / ideas |
| --- | --- |
| KEEP | Hybrid retrieval / RAG for now; citation verification; lifecycle controls; evidence sufficiency; high-risk claim guard; evidence-set reasoning; corrective false-premise handling; human review; AUTO / REVIEW / ABSTAIN |
| UPGRADE | Strong primary orchestrator; bounded specialist tools; long-context reasoning where useful; risk- and complexity-aware model routing; future controlled computer-use workflows |
| REDUCE / REPLACE | Excessive multi-agent chains; unnecessary custom orchestration; repetitive prompt scaffolding; custom runtime infrastructure where managed services provide equivalent capability |
| IGNORE | “Long context means RAG is dead”; “every capability needs its own agent”; adopting new frameworks without measurable NHS operational value |

These are provisional review decisions. Architecture v1 remains the tested baseline until changes pass evaluation.

### Economic principle

> Spend money on useful intelligence and NHS-specific assurance, not unnecessary AI plumbing.

### Emerging USP and NHS manager value

A model-flexible, evidence-governed NHS operational intelligence copilot that reduces unnecessary AI complexity while preserving auditability, policy safety and human accountability.

The system should reduce time spent gathering, reconciling and interpreting operational information while keeping the manager accountable for the final decision.

### Future business metrics to measure

- Management briefing preparation time saved.
- Analyst minutes saved.
- Manual data sources avoided.
- Policy-search time reduced.
- Citation accuracy.
- Unsafe answers blocked.
- Appropriate human escalations.
- Cost per governed query.

These are future measurement targets, not benefits already demonstrated by the prototype.

### Model replaceability goal

The assurance layer should remain stable enough that a future frontier model can replace the current intelligence model without rebuilding the whole governance system, provided the replacement passes evaluation.

### Day 2 Plan Recorded at Day 1 Completion

**RAG, retrieval and evidence architecture review.** Examine hybrid retrieval, reranking, long-context alternatives, graph / relationship retrieval, contextual retrieval, evidence architecture and which current retrieval components still earn their place.

---

## Week 19 — COMPLETE: Grounded Answer Governance

**Project:** Healthcare Document Intelligence / RAG Assistant  
**Theme:** Grounded answer governance, citation verification, high-risk claim protection, semantic rescue, and evidence-set reasoning.  
**Progress at Week 19 completion:** Week 19 = COMPLETE; Week 20 was next. See the Week 20 Day 2 record above for current progress.  
**Status recorded:** 27 September 2026, using the verified final results supplied by the project owner.

### Claim-level evidence sufficiency

Added deterministic claim/evidence checks for contradiction and precedence claims, relationships, quantitative and current/external claims, and mandatory procedural claims. False-abstention evaluation is complete.

Final Hybrid Rescue performance on the controlled 75-case synthetic retrieval benchmark:

| Metric | Result |
| --- | ---: |
| Top-1 | 82.22% |
| Top-k | 82.22% |
| Abstention accuracy | 100% |
| Active-document compliance | 100% |

### Citation verification

Claim-level citation verification validates citation resolution, document/chunk identity, lifecycle safety, lexical support and the answer-level outcome. Outcomes include `PASS`, `REVIEW_REQUIRED` and `ABSTAIN`.

### High-risk claim guard

Deterministic checks detect unsupported numbers, mandatory wording, actors, actions, negation and prohibitions. The high-risk guard experiment achieved **15/15** on the controlled test set.

### Guarded semantic citation rescue

Semantic rescue runs only after citation and lifecycle safety checks. It uses `sentence-transformers/all-MiniLM-L6-v2`, with a semantic rescue threshold of **0.75** and lexical support threshold of **0.60**. Lifecycle-unsafe evidence cannot be rescued semantically.

The production-code citation benchmark recorded **14/15 correct (93.3%)**, **0 false acceptances** and **1 false rejection**. This describes testing of the project implementation on synthetic cases, not production NHS validation or deployment. The remaining difficult case, **CIT010**, required evidence-set reasoning rather than ordinary single-citation verification.

### Evidence-set relationship reasoning

Created in the RAG project: `src/governance/evidence_set_relationship.py`.

Supported relationships: `CONFLICT`, `COMPLEMENTS`, `REPLACES`, `TAKES_PRECEDENCE`.

Possible outcomes: `RELATIONSHIP_SUPPORTED`, `RELATIONSHIP_NOT_ESTABLISHED`, `REVIEW_REQUIRED`.

Draft, Superseded, Archived or unconfirmed evidence cannot automatically establish an authoritative relationship.

### Corrective false-premise handling

Created in the RAG project: `src/governance/corrective_false_premise.py`.

The system can validate whether a user's assumed document relationship is established before reasoning from it. Example safe correction:

> The available evidence does not establish that DOC-003 and DOC-011 conflict.

Absence of documented conflict does **not** prove that no conflict exists. The system states only that the supplied evidence does not establish the alleged relationship. The new relationship and corrective-validation tests do not, by themselves, establish a new end-to-end citation benchmark score.

### Final testing status

| Validation | Result |
| --- | ---: |
| Evidence-set relationship tests | 10 passed |
| Corrective false-premise tests | 8 passed |
| Combined Day 6 relationship tests | 18 passed |
| Full project regression | **338 passed** |

### Week 19 engineering principle

> Verify the premise before reasoning from it.

### Current governed architecture

```text
Question
→ Scope Gate
→ Retrieval
→ Evidence Sufficiency
→ Pre-generation Governance
→ Answer Generation
→ Citation Verification
→ High-Risk Claim Guard
→ Guarded Semantic Rescue
→ Evidence-Set Relationship Validation
→ Corrective False-Premise Validation
→ Post-generation Governance
→ AUTO_ANSWER / REVIEW_REQUIRED / ABSTAIN
```

### Week 20 Plan Recorded at Week 19 Completion — Technology & Architecture Refresh Gate

Review frontier models, agents, RAG, retrieval, Microsoft Fabric / Azure, healthcare regulation, NHS digital strategy and deployment practices. Explore cross-pollination from aviation, banking, cybersecurity, logistics, manufacturing and other high-reliability industries.

Use four decisions: **KEEP / UPGRADE / REPLACE / IGNORE**.

Determine which architecture components remain valid, which should be upgraded, what is obsolete, which new capabilities genuinely improve the NHS project, and which technology is hype and should be ignored.

The benchmark results remain controlled prototype evidence. They do not demonstrate production readiness or NHS subject-matter-expert validation.

---

## Week 19 — Governed Evidence Retrieval & Targeted Rescue (Earlier Milestone)



The Week 18 retrieval benchmark was expanded from 14 to 38 controlled evaluation cases.



The expanded benchmark includes:



- clear single-document questions;

- paraphrased operational questions;

- ambiguous operational questions;

- cross-document questions;

- lifecycle conflicts;

- questions where the corpus contains no evidence;

- clinical out-of-scope questions;

- current external-information questions;

- adversarial prompts.



---



# Scope Control



A deterministic query-scope layer separates:



- questions appropriate for the operational assistant;

- clinical/prescribing questions;

- current external-information questions.



Important engineering finding:



A question being in scope does not mean the system has sufficient evidence to answer it.



Examples:



Q029 — cybersecurity incident procedure  

Q030 — electronic patient record system failure  

Q031 — medical oxygen supply failure



These questions are operationally valid but the current corpus does not contain specific supporting evidence.



They therefore require evidence-based abstention rather than scope rejection.



---



# Evidence Sufficiency



A deterministic concept-first evidence-sufficiency layer was added.



The system now distinguishes:



1. OUT_OF_SCOPE

2. IN_SCOPE + SUFFICIENT EVIDENCE

3. IN_SCOPE + INSUFFICIENT EVIDENCE



Similarity score alone was rejected as the abstention rule.



Observed score overlap demonstrated why.



Unsupported example:



- Q031 top semantic similarity ≈ 0.567



Valid answerable examples:



- Q037 ≈ 0.500

- Q026 ≈ 0.530

- Q036 ≈ 0.548



Therefore a simple similarity threshold would incorrectly reject valid questions.



---



# Evidence-Sufficiency Engineering Principle



Query eligibility and evidence sufficiency are different safety problems.



A question may be appropriate for the NHS operational scope while still requiring abstention because the available corpus does not substantiate the requested subject.



The system should not answer merely because it retrieves vaguely related operational documents.



---



# Multi-Document Retrieval Finding



## Q027



Question:



“How should severe weather pressure and ambulance handover disruption be considered together?”



Initial semantic/hybrid retrieval found strong ambulance-handover evidence but failed to retain severe-weather evidence.



The evidence-sufficiency layer correctly detected:



- ambulance_handover: present

- severe_weather: missing



Result:



INSUFFICIENT EVIDENCE



This exposed a retrieval problem rather than a scope or evidence-checker problem.



---



# Failed Experiment — Global RRF Reranking



A hybrid-specific RRF-first reranker was tested.



It successfully recovered severe-weather evidence for Q027.



However, it caused wider retrieval regressions.



Hybrid before global RRF reranking:



- Top-1: 75.0%

- Top-k: 87.5%



Hybrid after global RRF reranking:



- Top-1: 70.8%

- Top-k: 75.0%



Engineering conclusion:



A global ranking change solved one difficult case but degraded overall retrieval quality.



The experiment was therefore rejected as the default strategy.



---



# Successful Experiment — Targeted Evidence Rescue



A targeted Hybrid Rescue strategy was developed.



Flow:



Question  

→ Scope Gate  

→ Original Hybrid Retrieval  

→ Evidence Sufficiency



If evidence is sufficient:



→ keep original Hybrid result unchanged



If evidence is insufficient:



→ invoke RRF/BM25 rescue  

→ add missing evidence conservatively  

→ re-check evidence sufficiency



If evidence remains insufficient:



→ ABSTAIN



---



# Q027 Rescue Result



Initial evidence:



- Decision: INSUFFICIENT

- Missing concept: severe_weather



Rescue attempted:



- Yes



Rescued document:



- DOC-009 — Severe Weather Operational Plan



Final evidence:



- Decision: SUFFICIENT



Final evidence documents:



- DOC-008

- DOC-008

- DOC-009



This preserved the strong normal Hybrid path while recovering missing evidence only when required.



---



# Final 38-Case Governed Benchmark



| Method | Top-1 | Top-k | Abstention | Active-only |

|---|---:|---:|---:|---:|

| Semantic | 75.0% | 87.5% | 100% | 100% |

| Keyword | 41.7% | 62.5% | 100% | 100% |

| Hybrid | 75.0% | 87.5% | 100% | 100% |

| RRF-only | 70.8% | 75.0% | 100% | 100% |

| Hybrid Rescue | 79.2% | 91.7% | 100% | 100% |



At this earlier milestone, Hybrid Rescue was the strongest experimental retrieval method on the controlled 38-case benchmark.



It has not yet been promoted to the default retrieval strategy.



---



# Validation Status



Earlier retrieval milestone validation (retained history):



- 40 focused evidence-sufficiency tests passed

- 250 full tests passed after evidence integration

- 11 focused rescue tests passed

- 270 full tests passed before benchmark integration

- 272 tests passed after Hybrid Rescue benchmark integration



Evaluation set at that earlier milestone:



- 38 controlled cases



---



# Important Engineering Findings



## Finding 1 — Scope and evidence are separate



Scope control answers:



“Is this type of question appropriate for the system?”



Evidence sufficiency answers:



“Do the retrieved documents actually support the requested subject?”



These must remain separate controls.



---



## Finding 2 — Similarity does not equal evidence



High semantic similarity does not prove that the retrieved document contains sufficient evidence to answer a question.



---



## Finding 3 — Retrieval quality and answer safety are separate



A retrieval system can return relevant-looking documents while still lacking sufficient evidence for a safe answer.



---



## Finding 4 — Global optimisation can create regressions



Changing the ranking strategy globally fixed Q027 but damaged several previously strong cases.



Local improvements must therefore be tested against the entire benchmark.



---



## Finding 5 — Conditional rescue can outperform replacement



Targeted evidence rescue preserved the stronger baseline retrieval behavior while recovering missing evidence only when necessary.



---



## Finding 6 — Failed experiments are useful evidence



The failed global RRF experiment explained why the final conditional-rescue architecture was needed.



Engineering failures should be preserved as design evidence rather than hidden.



---



# NHS Relevance



For an NHS operational assistant, finding a vaguely related document is not sufficient.



A governed system should be able to say:



- this question is outside my permitted scope;

- this question is appropriate, but I do not have adequate evidence;

- I have sufficient active evidence to continue;

- human review is required.



This supports safer operational decision support and clearer accountability.



---



# Current Limitations



The current system:



- uses synthetic operational documents;

- has 75 controlled synthetic retrieval cases and a 15-case citation benchmark;

- uses deterministic concept vocabularies;

- has not been validated by NHS subject-matter experts;

- has not been evaluated against a large real NHS document collection;

- does not prove factual entailment merely from concept coverage;

- has not been production deployed;

- does not yet include production monitoring;

- does not yet include live NHS integrations.



Hybrid Rescue remains experimental.



The benchmark results must not be presented as production NHS performance.



---



# Current Skills Being Developed



## Technical



- Python

- SQL

- PostgreSQL

- RAG

- embeddings

- semantic retrieval

- BM25

- Reciprocal Rank Fusion

- hybrid retrieval

- deterministic reranking

- evidence sufficiency

- retrieval evaluation

- abstention design

- retrieval rescue

- automated testing

- auditability

- AI governance



## Healthcare / NHS



- operational escalation

- winter pressure

- workforce pressure

- bed capacity

- ambulance handover

- severe weather disruption

- operational governance

- document lifecycle authority

- evidence quality

- human accountability



---



# Current Portfolio Evidence



I can demonstrate:



- healthcare document ingestion;

- metadata and lifecycle governance;

- chunking and embedding pipelines;

- semantic and keyword retrieval;

- hybrid retrieval;

- RRF experiments;

- controlled benchmark design;

- retrieval failure analysis;

- deterministic scope control;

- evidence-sufficiency controls;

- abstention;

- targeted retrieval rescue;

- human-review routing;

- structured auditability;

- regression testing;

- evidence-based engineering decisions.



---



# Current Interview Story



Situation:



A multi-document NHS operational question required both severe-weather and ambulance-handover evidence.



Task:



Improve retrieval coverage without weakening safety or degrading the wider benchmark.



Action:



I compared semantic retrieval, BM25, Hybrid and RRF behavior.



I found that semantic retrieval missed severe-weather evidence while BM25 found it.



I rejected a global RRF-first ranking change after testing showed that it fixed the individual case but caused wider benchmark regressions.



I instead developed an evidence-aware conditional rescue mechanism that invokes alternate retrieval only when the normal evidence set is insufficient.



Result:



On the controlled 38-case synthetic benchmark, Hybrid Rescue achieved:



- Top-1: 79.2%

- Top-k: 91.7%

- Abstention: 100%

- Active-only lifecycle compliance: 100%



These are prototype benchmark results and not production NHS performance.



---



# Current Questions



1. Does Hybrid Rescue continue to outperform on a substantially larger benchmark?

2. How should evidence sufficiency be tested against harder paraphrases?

3. How should conflicting evidence across documents be detected?

4. How should NHS SME review be incorporated into evaluation?

5. How should citation verification be strengthened?

6. How should human-review feedback be captured and reused?

7. How should this governed retrieval architecture evolve into an agentic operational assistant without excessive autonomy?



---



# Immediate Next Technical Priority



Week 21 — evaluate reranking, bounded agentic retrieval and relationship-aware retrieval; build a clean orchestrator and Architecture v2 integration tests; compare Architecture v1 vs v2. Central question: does Architecture v2 retrieve better evidence without increasing unsafe behaviour?

Earlier priority (completed): expand beyond 38 cases. The retrieval benchmark now contains 75 cases; promotion of Hybrid Rescue remains a separate decision.



Do not add unrelated technologies simply to increase project complexity.



The next improvements should be driven by measured failure modes.



---



# Second Brain Workflow



Continue:



## Capture



Record:



- what was learned;

- what was built;

- what failed;

- benchmark evidence;

- important implementation decisions.



## Connect



Connect lessons across:



- RAG;

- NHS governance;

- operational intelligence;

- future agents;

- Sovereign NHS Operational Copilot.



## Critique



Identify:



- weak assumptions;

- missing validation;

- safety risks;

- benchmark weaknesses;

- unresolved engineering questions.



## Compress



Convert the work into:



- engineering principles;

- interview evidence;

- architecture decisions;

- reusable patterns;

- future experiments.



---



# Current Restart Point

Week 19 = COMPLETE. Week 20 = COMPLETE through Day 6 closeout. Week 21 = NEXT: Architecture v2 implementation and comparative evaluation.

Latest verified regression baseline: **338 passed**. Day 1 was documentation-only; tests were not rerun. Architecture v1 remains the tested Week 19 baseline.

Day 2 principle retained: **Do not replace a strong hybrid retrieval foundation. Add smarter behaviour around it.**

Day 1 principle retained: **Simplify the intelligence layer, preserve the assurance layer.** Week 19 principle retained: **Verify the premise before reasoning from it.**

The Week 20 Day 6 closeout above is the latest status. Architecture v2 remains a proposed direction, not an implemented or validated replacement. The Day 1 and Day 2 reviews, Week 19 completion record and earlier milestone snapshots are retained as history. Current principle: simple intelligence, strong assurance. Operating model: Detect → Prioritise → Explain → Verify → Human Decide → Learn.

## Earlier Restart Snapshot — After Claim-Level Evidence Upgrade



Week 19 governed retrieval work is complete through the Hybrid Rescue experiment.



Latest status:

- 75-case benchmark operational
- scope gate operational
- topic-level and claim-level evidence sufficiency operational
- targeted evidence rescue operational
- lifecycle protection operational
- 276 tests passing
- Hybrid Rescue currently strongest experimental retrieval method on the controlled benchmark
- Hybrid Rescue Top-1: 80.0%
- Hybrid Rescue Top-k: 80.0%
- Abstention: 100%
- Active-only: 100%

Next:

Test whether claim-level evidence checks create false abstentions on harder answerable questions before expanding the rule set or promoting Hybrid Rescue further.



## Week 19 — Claim-Level Evidence Upgrade

The 75-case benchmark exposed four cases where topic-level evidence was not enough:

- Q063 — fabricated workforce conflict
- Q064 — fabricated policy conflict
- Q065 — supported ambulance-handover topic plus unsupported current financial penalty
- Q067 — supported infection-surge topic plus unsupported exact numerical trigger

The evidence layer was upgraded from topic-level sufficiency to claim-level completeness.

New deterministic checks cover:

- contradiction / precedence claims
- relationship claims
- quantitative claims
- current / external requirements
- mandatory procedural conditions

Validation:

- 44 focused evidence tests passed
- 276 full project tests passed

75-case Hybrid Rescue result at the claim-level upgrade milestone:

- Top-1: 80.0%
- Top-k: 80.0%
- Abstention: 100%
- Active-only: 100%

Key learning:

Evidence sufficiency must be evaluated at the level of requested claims and relationships, not only detected topics.

Next priority:

Test whether claim-level checks cause false abstentions on harder answerable questions before expanding the rule set further.


## Week 19 — Day 3: Citation Verification & Grounded Answer Governance

Day 3 added a post-generation safety layer to the Healthcare Document Intelligence RAG system.

Completed:
- deterministic citation verification
- claim outcomes:
  - SUPPORTED
  - PARTIALLY_SUPPORTED
  - UNSUPPORTED
  - CITATION_MISMATCH
- correct document and chunk verification
- lifecycle-safe citation checks
- answer-level PASS / REVIEW_REQUIRED / ABSTAIN
- post-generation governance integration
- monotonic safety rule: later stages can preserve or downgrade safety decisions, but cannot upgrade an unsafe decision
- 16 citation-verification tests passed
- 28 combined citation/governance tests passed
- 310 full project tests passed
- local project and GitHub main synchronized

Governed RAG architecture at the Day 3 milestone:

Question
→ Scope Gate
→ Retrieval
→ Evidence Sufficiency
→ Pre-generation Governance
→ Answer Generation
→ Citation Verification
→ Post-generation Governance
→ AUTO_ANSWER / REVIEW_REQUIRED / ABSTAIN

Key learning:

Good retrieval does not guarantee a grounded final answer.

Every material answer claim should be traceable to the correct supporting evidence and lifecycle-safe citation.

Next priority:

Evaluate citation verification on realistic generated answers and measure false-positive and false-negative grounding decisions before increasing verifier complexity.