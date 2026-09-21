\# Cross-Project Connections



\## Purpose



This document connects engineering lessons across the major projects in the 18-month Health \& Care AI Engineer roadmap.



The goal is to identify reusable principles so each project strengthens the next one.



\---



\# Project Progression



NHS ICB OPEL Level Predictor

↓

NHS Operational Data Platform

↓

Healthcare Document Intelligence / RAG

↓

Agentic Operational Assistant

↓

NHS Sovereign Operational Intelligence \& Evidence Copilot



These should be treated as an evolving system rather than unrelated portfolio projects.



\---



\# Connection 1 — Evidence Quality



\## Lesson from Healthcare Document Intelligence



Semantic similarity does not equal sufficient evidence.



A result can look relevant while still being inappropriate for answering the user's actual question.



\## Connection to OPEL Predictor



A model prediction should not automatically be treated as sufficient evidence for an operational decision.



A high predicted OPEL level should be accompanied by:



\- input quality;

\- feature availability;

\- confidence;

\- contributing factors;

\- data freshness;

\- limitations.



\## Connection to Operational Data Platform



The platform must expose whether the underlying data is:



\- complete;

\- current;

\- validated;

\- missing;

\- anomalous;

\- trustworthy enough for downstream use.



\## Connection to Future Agent



The agent must not act simply because a tool returned something plausible.



It should ask:



\- Is the evidence sufficient?

\- Is the source authoritative?

\- Is the information current?

\- Does the evidence support this action?



\## Reusable Principle



Plausibility is not proof.



\---



\# Connection 2 — Authority vs Relevance



\## Lesson from Healthcare Document Intelligence



A document may be relevant but not authoritative.



Draft, Superseded, and Archived documents should not normally drive authoritative answers.



\## Connection to Operational Data Platform



Data sources also have authority.



Examples:



\- approved warehouse table;

\- temporary staging table;

\- manually edited spreadsheet;

\- stale extract;

\- unofficial local copy.



The system should know which source is authoritative.



\## Connection to Future Agent



The agent should not treat every connected system or retrieved source as equally trustworthy.



Tool outputs may require:



\- source ranking;

\- permission checks;

\- lifecycle checks;

\- freshness checks;

\- provenance.



\## Reusable Principle



AI systems must reason about source authority, not only information relevance.



\---



\# Connection 3 — Human Review



\## Lesson from Healthcare Document Intelligence



The first review policy was too conservative because nearly every query was sent for human review.



The improved policy used evidence quality and ambiguity.



\## Connection to OPEL Predictor



Not every prediction needs manual escalation.



Potential future routing:



LOW RISK

→ normal monitoring



MEDIUM UNCERTAINTY

→ analyst review



HIGH OPERATIONAL IMPACT

→ senior operational review



\## Connection to Future Agent



Human review should be based on:



\- uncertainty;

\- impact;

\- reversibility;

\- evidence quality;

\- policy constraints.



It should not simply be:



all automation



or



all human review.



\## Reusable Principle



Use selective human oversight rather than blanket automation or blanket review.



\---



\# Connection 4 — Failed Experiments



\## Lesson from Healthcare Document Intelligence



RRF-only fusion performed worse than expected.



This disproved the hypothesis that the reranker was harming performance.



\## Connection to OPEL Predictor



A model experiment that performs worse is still useful if it eliminates a weak approach.



\## Connection to Operational Data Platform



A schema, validation rule, or analytical query may need to be rejected after testing.



\## Connection to Future Agent



Tool strategies and planning methods should be experimentally compared rather than assumed to be better because they are newer or more complex.



\## Reusable Principle



A failed hypothesis is useful engineering evidence.



\---



\# Connection 5 — Complexity



\## Lesson from Healthcare Document Intelligence



Hybrid retrieval did not outperform semantic retrieval on the current benchmark.



\## Connection to Operational Data Platform



Adding more infrastructure does not automatically improve analytical value.



Examples:



\- unnecessary services;

\- premature distributed architecture;

\- excessive orchestration;

\- unnecessary cloud complexity.



\## Connection to Future Agent



More agents do not automatically create a better system.



Multi-agent architecture should only be introduced when:



\- tasks are meaningfully separable;

\- coordination adds measurable value;

\- evaluation shows improvement.



\## Reusable Principle



Complexity must earn its place through measurable value.



\---



\# Connection 6 — Scope Boundaries



\## Lesson from Healthcare Document Intelligence



A scope gate prevented operational documents from being used to answer medication or prescribing questions.



\## Connection to OPEL Predictor



The predictor should be explicit about what it predicts and what it does not predict.



It should not be presented as:



\- clinical diagnosis;

\- patient-level treatment advice;

\- autonomous escalation authority.



\## Connection to Operational Data Platform



Datasets should have defined intended and prohibited uses.



\## Connection to Future Agent



The agent will need explicit tool and action boundaries.



Examples:



Allowed:



\- retrieve operational guidance;

\- summarise evidence;

\- identify anomalies;

\- draft escalation options.



Potentially restricted:



\- send external communications;

\- change operational records;

\- trigger workflows;

\- make high-impact decisions.



\## Reusable Principle



Scope should be designed explicitly rather than assumed.



\---



\# Connection 7 — Auditability



\## Lesson from Healthcare Document Intelligence



Every decision can record:



\- question;

\- evidence;

\- scores;

\- scope;

\- decision;

\- reason;

\- reviewer status.



\## Connection to OPEL Predictor



Prediction records could capture:



\- model version;

\- input timestamp;

\- prediction;

\- confidence;

\- feature values;

\- explanation;

\- reviewer outcome.



\## Connection to Operational Data Platform



Data processing should preserve:



\- source lineage;

\- load batch;

\- validation result;

\- transformation history.



\## Connection to Future Agent



Every significant agent action should eventually record:



\- user request;

\- retrieved evidence;

\- tools called;

\- action proposed;

\- verification result;

\- human approval;

\- final outcome.



\## Reusable Principle



If the system cannot explain what happened later, governance is weak.



\---



\# Connection 8 — Evaluation Before Deployment



\## Lesson from Healthcare Document Intelligence



The 14-case benchmark exposed weaknesses that normal demonstrations would not have shown.



\## Connection to OPEL Predictor



Performance should be tested against:



\- representative cases;

\- edge cases;

\- missing data;

\- unusual pressure patterns;

\- temporal drift.



\## Connection to Operational Data Platform



Data pipelines should be tested for:



\- duplicates;

\- missing dates;

\- impossible values;

\- orphan records;

\- schema failures.



\## Connection to Future Agent



Agent evaluation must include:



\- correct actions;

\- incorrect actions;

\- unnecessary actions;

\- failure recovery;

\- tool misuse;

\- unsupported claims;

\- human intervention.



\## Reusable Principle



Evaluation is part of system design, not a final checkbox.



\---



\# Emerging Unified Architecture



The projects are starting to form one system:



Operational Data

↓

Validated Data Platform

↓

Predictive Intelligence

↓

Document / Policy Evidence

↓

Evidence Sufficiency

↓

Operational Recommendation

↓

Human Review

↓

Action

↓

Audit Trail



This is the foundation for the future:



NHS Sovereign Operational Intelligence \& Evidence Copilot



\---



\# Cross-Project Design Principles



1\. Plausibility is not proof.

2\. Relevance is not authority.

3\. Complexity must earn its place.

4\. Failed hypotheses create knowledge.

5\. Human oversight should be selective.

6\. Scope boundaries should be explicit.

7\. Auditability should be designed from the beginning.

8\. Evaluation should precede trust.

