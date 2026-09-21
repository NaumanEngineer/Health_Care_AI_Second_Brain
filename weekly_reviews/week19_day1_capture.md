\# Week 19 Day 1 — Capture



\## Source Period



Weeks 17–18



Primary project:



Healthcare Document Intelligence / RAG Assistant



\---



\# 1. What I Built



I built a governed healthcare document intelligence system focused on operational policy and evidence retrieval.



The pipeline evolved into:



Documents  

↓  

Extraction  

↓  

Cleaning  

↓  

Chunking  

↓  

Metadata  

↓  

Embeddings  

↓  

Retrieval  

↓  

Lifecycle Filtering  

↓  

Reranking  

↓  

Evidence Assessment  

↓  

AUTO\_ANSWER / REVIEW\_REQUIRED / ABSTAIN  

↓  

Grounded Answer or Human Review  

↓  

Audit Record



\---



\# 2. What I Tested



I compared four retrieval approaches:



1\. Semantic retrieval

2\. BM25 keyword retrieval

3\. Hybrid retrieval

4\. RRF-only hybrid retrieval



The benchmark contained 14 controlled evaluation cases.



It included:



\- operational escalation;

\- workforce pressure;

\- bed capacity;

\- winter pressure;

\- business continuity;

\- governance;

\- lifecycle conflict;

\- cross-document reasoning;

\- clinical out-of-scope questions;

\- unsupported current-information questions.



\---



\# 3. Final Retrieval Results



\## Semantic



\- Top-1: 70%

\- Top-k: 90%

\- Abstention: 100%

\- Active-only: 100%



\## BM25



\- Top-1: 20%

\- Top-k: 40%

\- Abstention: 100%

\- Active-only: 100%



\## Hybrid



\- Top-1: 70%

\- Top-k: 90%

\- Abstention: 100%

\- Active-only: 100%



\## RRF-only



\- Top-1: 40%

\- Top-k: 50%

\- Abstention: 100%

\- Active-only: 100%



\---



\# 4. Important Failure



The original retrieval system had:



0% abstention success.



Out-of-scope questions still returned plausible operational documents.



Examples included:



\- medication prescribing;

\- antibiotic dosing;

\- current NHS England leadership information.



This showed that retrieval relevance alone was not a sufficient safety control.



\---



\# 5. What I Initially Assumed



I initially expected similarity thresholds to help distinguish answerable and unsupported questions.



That assumption was weak.



A valid operational query had a top semantic score around:



0.5858



while an unsupported medication question had a top semantic score around:



0.5806



The scores were almost identical.



Therefore:



semantic similarity alone could not reliably determine whether the system had sufficient evidence to answer.



\---



\# 6. Control Introduced



I introduced a deterministic query-scope gate.



The system separates:



IN\_SCOPE



from:



OUT\_OF\_SCOPE



before normal retrieval-based answering.



This improved abstention success from:



0%



to:



100%



on the controlled benchmark.



Semantic retrieval performance remained:



\- Top-1: 70%

\- Top-k: 90%



\---



\# 7. Retrieval Experiment Finding



Hybrid retrieval did not outperform semantic retrieval.



Both achieved:



\- 70% Top-1

\- 90% Top-k



This demonstrated that additional retrieval complexity does not automatically improve performance.



\---



\# 8. RRF Finding



I tested RRF-only fusion because I suspected the post-fusion reranker might be damaging hybrid performance.



The hypothesis was wrong.



RRF-only performance fell to:



\- 40% Top-1

\- 50% Top-k



This showed that the existing reranking stage was adding useful value.



\---



\# 9. Lifecycle Governance Finding



All evaluated retrieval methods maintained:



100% Active-only compliance.



This reinforced an important distinction:



relevance is not the same as authority.



A document may be semantically relevant but still be:



\- Draft;

\- Superseded;

\- Archived;

\- inappropriate for authoritative use.



\---



\# 10. Human Review Problem



The first human-review rule was too conservative.



The initial rule effectively treated:



three retrieved documents



as:



REVIEW\_REQUIRED.



Because retrieval normally returned three results, this produced:



\- AUTO\_ANSWER: 0

\- REVIEW\_REQUIRED: 11

\- ABSTAIN: 3



This was not useful automation.



\---



\# 11. Human Review Improvement



I replaced the crude document-count rule with evidence-strength rules.



Current prototype AUTO\_ANSWER requirements include:



\- query is in scope;

\- evidence is Active;

\- top semantic similarity >= 0.65;

\- top-to-second score gap >= 0.05;

\- no explicit cross-document reasoning trigger;

\- no lifecycle warning.



Final distribution:



\- AUTO\_ANSWER: 3

\- REVIEW\_REQUIRED: 8

\- ABSTAIN: 3



The three AUTO\_ANSWER cases related to:



\- bed-capacity escalation;

\- business continuity;

\- winter-pressure guidance.



\---



\# 12. Auditability



I added structured audit records containing:



\- query ID;

\- question;

\- timestamp;

\- retrieval method;

\- scope result;

\- decision outcome;

\- decision reason;

\- document IDs;

\- evidence metadata;

\- retrieval scores;

\- reviewer status;

\- reviewer action fields.



This makes the decision process inspectable rather than opaque.



\---



\# 13. Main Engineering Lessons



\## Lesson 1



Semantic similarity does not equal sufficient evidence.



\---



\## Lesson 2



Document relevance does not equal document authority.



\---



\## Lesson 3



More retrieval complexity does not automatically improve quality.



\---



\## Lesson 4



Failed hypotheses are useful evidence.



The RRF-only experiment disproved the assumption that the reranker was harming hybrid retrieval.



\---



\## Lesson 5



Human review should be triggered by uncertainty and evidence quality, not simply by the number of retrieved documents.



\---



\## Lesson 6



Governance controls should be measurable and testable.



\---



\## Lesson 7



A system that knows when not to answer may be safer than a system that always produces a plausible response.



\---



\# 14. Current Limitations



The current results are not production validation.



Limitations include:



\- synthetic documents;

\- only 14 evaluation cases;

\- manually designed scope rules;

\- prototype confidence thresholds;

\- no NHS operational expert validation;

\- no real clinical deployment;

\- no large-scale document corpus;

\- no production monitoring.



Therefore:



100% abstention means 100% on the current controlled benchmark only.



\---



\# 15. Things I Do Not Want to Forget



1\. Q007 demonstrated that high semantic similarity can still represent the wrong task scope.



2\. Q002 and Q007 had almost identical top semantic scores, which disproved the idea that a simple threshold would solve abstention.



3\. Hybrid retrieval added complexity without measurable aggregate improvement.



4\. RRF-only performed worse, proving the reranker was useful.



5\. The first human-review policy was too conservative and had to be recalibrated.



6\. Governance became stronger when decisions were converted into explicit, testable rules.



7\. The system should remain an operational evidence assistant, not an autonomous decision-maker.



\---



\# 16. Future Questions Created by This Work



1\. How should score thresholds be calibrated on a much larger evaluation set?



2\. How should human reviewer feedback be captured?



3\. How should conflicting evidence between two Active documents be detected?



4\. How should the system identify when evidence is incomplete rather than merely weak?



5\. How should citation correctness be automatically checked?



6\. How should review decisions feed future evaluation without creating unsafe self-learning?



7\. How should the future agentic assistant use this evidence layer without bypassing governance controls?

