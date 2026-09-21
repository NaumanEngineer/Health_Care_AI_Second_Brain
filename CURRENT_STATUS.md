\# Health \& Care AI Engineering — Current Status



\## Current Stage



\- Roadmap: 18-Month Health \& Care AI Engineer

\- Current Week: Week 19

\- Current Focus: Health \& Care AI Engineering Second Brain

\- Study Model: Learn → Build → Test → Govern → Document → Reuse



\---



\# Current Flagship Progression



1\. NHS ICB OPEL Level Predictor

2\. NHS Operational Data Platform

3\. Healthcare Document Intelligence / RAG Assistant

4\. Agentic Operational Assistant

5\. NHS Sovereign Operational Intelligence \& Evidence Copilot



The objective is to evolve these systems into one coherent NHS operational intelligence and evidence platform rather than build disconnected projects.



\---



\# Most Recently Completed Work



\## Week 18 — Governed Retrieval \& Human Review



Completed:



\- semantic retrieval evaluation;

\- BM25 keyword retrieval;

\- hybrid retrieval;

\- RRF-only retrieval experiment;

\- lifecycle-aware evidence filtering;

\- query-scope control;

\- abstention handling;

\- human-review routing;

\- evidence-confidence rules;

\- structured governance audit records.



Final benchmark:



\- Semantic Top-1: 70%

\- Semantic Top-k: 90%

\- Abstention success: 100%

\- Active-only lifecycle compliance: 100%



Human-review distribution:



\- AUTO\_ANSWER: 3

\- REVIEW\_REQUIRED: 8

\- ABSTAIN: 3



\---



\# Important Engineering Findings



\## Finding 1



Semantic similarity does not equal sufficient evidence.



An out-of-scope question may still retrieve a semantically similar document.



\---



\## Finding 2



Document relevance does not equal document authority.



Lifecycle state such as Active, Draft, Superseded, or Archived must be considered separately from retrieval relevance.



\---



\## Finding 3



More retrieval complexity does not automatically improve performance.



Hybrid retrieval did not outperform the semantic baseline in the current benchmark.



\---



\## Finding 4



Human review should be triggered by uncertainty and evidence quality rather than simply by the number of documents retrieved.



\---



\## Finding 5



AI governance controls should be measurable and testable.



Examples include:



\- abstention rate;

\- lifecycle compliance;

\- evidence confidence;

\- review routing;

\- audit records.



\---



\# Current Limitations



The current Healthcare Document Intelligence benchmark:



\- uses synthetic documents;

\- contains only 14 evaluation cases;

\- uses prototype confidence thresholds;

\- has not been validated by NHS operational experts;

\- has not been tested against large real-world document collections;

\- is not a production clinical system.



The 100% abstention result therefore applies only to the current controlled evaluation set.



\---



\# Current Skills Being Developed



\## Technical



\- Python

\- SQL

\- PostgreSQL

\- RAG

\- embeddings

\- semantic retrieval

\- BM25

\- hybrid retrieval

\- reranking

\- evaluation

\- testing

\- governance controls



\## Healthcare / NHS



\- operational escalation

\- winter pressure

\- workforce pressure

\- bed capacity

\- operational governance

\- evidence authority

\- human accountability



\---



\# Current Portfolio Evidence



I can currently demonstrate:



\- building a healthcare document ingestion pipeline;

\- metadata and document lifecycle governance;

\- chunking and embeddings;

\- semantic and keyword retrieval;

\- controlled hybrid retrieval experiments;

\- evaluation benchmark design;

\- failure analysis;

\- abstention controls;

\- human-review routing;

\- structured auditability.



\---



\# Current Interview Story



I tested multiple retrieval approaches and discovered that better retrieval alone did not solve unsafe evidence selection.



Out-of-scope clinical questions could still retrieve operational documents with reasonable semantic similarity.



I introduced a deterministic scope-control layer, improving abstention success from 0% to 100% on the controlled benchmark while maintaining retrieval performance.



I then added AUTO\_ANSWER, REVIEW\_REQUIRED, and ABSTAIN governance decisions with structured audit records.



\---



\# Current Questions



1\. How should evidence sufficiency be evaluated on a larger benchmark?

2\. How should human-review feedback be captured and reused?

3\. How should conflicting evidence across documents be detected?

4\. How should the system evolve toward an agentic operational assistant without giving it excessive autonomy?

5\. How should evaluation evolve when real NHS-style documents are introduced?



\---



\# Next Technical Direction



Continue improving the Healthcare Document Intelligence system before moving into full agentic workflows.



Priority areas:



1\. stronger evidence evaluation;

2\. citation verification;

3\. human-review workflow;

4\. larger benchmark;

5\. richer operational document corpus;

6\. preparation for later agentic tool use.



\---



\# Second Brain Workflow



Every week:



\## Capture



Record:



\- what was learned;

\- what was built;

\- what failed;

\- benchmark evidence;

\- decisions made.



\## Connect



Identify where lessons apply elsewhere.



\## Critique



Identify:



\- weak assumptions;

\- missing validation;

\- risks;

\- unresolved questions.



\## Compress



Convert the week's work into:



\- engineering principles;

\- interview evidence;

\- architecture decisions;

\- future experiments.



\---



\## Week 19 Day 1 Completed



Completed the first Second Brain cycle:



\- Capture

\- Connect

\- Critique

\- Compress



Key outputs:



\- healthcare project knowledge record;

\- cross-project connection map;

\- agentic design connection note;

\- Week 17–18 capture;

\- Week 19 Day 1 compressed review.



Primary next experiment:



Expand the evidence-quality benchmark from 14 cases to approximately 30–50 controlled cases.

















