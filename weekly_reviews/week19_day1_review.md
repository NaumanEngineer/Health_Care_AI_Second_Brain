\# Week 19 Day 1 — Review



\## Purpose



Compress the most important engineering knowledge from Weeks 17–18 and connect it to the future roadmap.



\---



\# 1. CRITIQUE



\## What worked well



\### Retrieval evaluation



The project moved beyond demonstration by comparing:



\- semantic retrieval;

\- BM25;

\- hybrid retrieval;

\- RRF-only retrieval.



This produced measurable evidence rather than assumptions.



\### Scope control



The deterministic query-scope gate addressed a real failure mode:



semantically related evidence could be retrieved for unsupported questions.



\### Human-review routing



The system evolved from blanket review toward selective automation using:



\- scope;

\- lifecycle;

\- evidence strength;

\- score separation;

\- cross-document reasoning.



\### Auditability



The system now records evidence and governance decisions rather than only producing an answer.



\---



\# 2. What remains weak



\## Benchmark size



The current benchmark contains only 14 cases.



This is useful for prototyping but too small to support strong production claims.



\---



\## Synthetic corpus



The documents are synthetic.



Real NHS documents may contain:



\- inconsistent formatting;

\- tables;

\- scanned pages;

\- amendments;

\- duplicated guidance;

\- local variations;

\- ambiguous authority.



\---



\## Confidence thresholds



The current prototype uses thresholds such as:



\- top similarity >= 0.65;

\- top-to-second score gap >= 0.05.



These were calibrated against the current small evaluation set.



They should not be treated as production thresholds.



\---



\## Scope rules



The current scope gate is deterministic.



It works well on the controlled benchmark but may not generalise to more subtle out-of-scope queries.



\---



\## Human review



REVIEW\_REQUIRED currently represents a routing decision.



A richer reviewer workflow is still needed.



Future questions include:



\- Who reviews?

\- What can they override?

\- How is reviewer feedback stored?

\- How is disagreement handled?

\- How does feedback improve evaluation?



\---



\## Operational validation



No NHS operational expert has validated the current behaviour.



Technical correctness does not automatically equal operational usefulness.



\---



\# 3. Five Engineering Principles



\## Principle 1 — Similarity is not sufficient evidence



A semantically similar result can still be unsuitable for answering the question.



\---



\## Principle 2 — Relevance is not authority



Evidence must also be checked for lifecycle, provenance, and approved status.



\---



\## Principle 3 — Complexity must earn its place



Hybrid retrieval did not outperform semantic retrieval.



RRF-only performed worse.



New components should be retained only when they improve measurable outcomes.



\---



\## Principle 4 — Human oversight should be selective



Systems should avoid both extremes:



\- automate everything;

\- send everything to humans.



Review should depend on uncertainty, impact, evidence quality, and policy constraints.



\---



\## Principle 5 — Governance should be executable



Governance becomes stronger when it exists as:



\- tests;

\- thresholds;

\- routing rules;

\- lifecycle checks;

\- audit records;



rather than only as written policy.



\---



\# 4. Three Interview Stories



\## Interview Story 1 — Unsafe retrieval



\### Situation



The RAG system retrieved plausible operational documents even when the question requested unsupported clinical information.



\### Task



Prevent the system from treating semantic relevance as sufficient evidence.



\### Action



I compared similarity scores across valid and invalid queries and found that simple thresholds could not reliably separate them.



I introduced a deterministic scope gate before evidence-based answering.



\### Result



Abstention success improved from 0% to 100% on the controlled benchmark while semantic retrieval remained at 70% Top-1 and 90% Top-k.



\### Lesson



Good AI engineering includes knowing when the system should not answer.



\---



\## Interview Story 2 — Hybrid retrieval experiment



\### Situation



I wanted to determine whether adding keyword retrieval and reciprocal-rank fusion improved semantic retrieval.



\### Task



Measure the value of additional retrieval complexity.



\### Action



I compared semantic, BM25, hybrid, and RRF-only retrieval across the same benchmark.



\### Result



Semantic and hybrid both achieved 70% Top-1 and 90% Top-k.



RRF-only fell to 40% Top-1 and 50% Top-k.



\### Lesson



More sophisticated architecture is not automatically better.



\---



\## Interview Story 3 — Human-review calibration



\### Situation



The first human-review policy routed every valid in-scope case to review.



\### Task



Create a more useful balance between automation and oversight.



\### Action



I analysed why cases were being escalated and replaced the crude document-count rule with confidence and score-gap controls.



\### Result



The final distribution became:



\- AUTO\_ANSWER: 3

\- REVIEW\_REQUIRED: 8

\- ABSTAIN: 3



\### Lesson



Human oversight should be driven by risk and uncertainty rather than blanket rules.



\---



\# 5. Two Unresolved Questions



\## Question 1



How should evidence-confidence thresholds be calibrated on a larger and more representative corpus?



\## Question 2



How should human-review feedback be converted into evaluation data without allowing unsafe self-learning?



\---



\# 6. One Next Experiment



Build a larger evidence-quality evaluation set.



Target:



at least 30–50 controlled cases covering:



\- clear single-document answers;

\- ambiguous questions;

\- cross-document questions;

\- lifecycle conflicts;

\- weak evidence;

\- no evidence;

\- clinical out-of-scope requests;

\- current external-information requests;

\- adversarial phrasing.



Measure:



\- retrieval accuracy;

\- abstention;

\- review routing;

\- lifecycle compliance;

\- false AUTO\_ANSWER rate.



\---



\# 7. Current Architecture Insight



The broader roadmap is converging toward:



Operational Data

↓

Validated Data Platform

↓

Predictive Intelligence

↓

Document and Policy Evidence

↓

Evidence Sufficiency

↓

Human Review

↓

Controlled Action

↓

Auditability



This is the foundation for the future NHS Sovereign Operational Intelligence \& Evidence Copilot.



\---



\# 8. Day 1 Compression



\## Five principles



1\. Similarity is not sufficient evidence.

2\. Relevance is not authority.

3\. Complexity must earn its place.

4\. Human oversight should be selective.

5\. Governance should be executable.



\## Three interview stories



1\. Scope-gate abstention improvement.

2\. Hybrid/RRF retrieval experiment.

3\. Human-review recalibration.



\## Two unresolved questions



1\. Larger-scale threshold calibration.

2\. Safe use of reviewer feedback.



\## One next experiment



Expand the evaluation set to 30–50 controlled evidence-quality cases.

