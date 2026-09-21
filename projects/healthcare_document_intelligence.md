\# Healthcare Document Intelligence / RAG Assistant



\## Purpose



Build a governed operational evidence assistant that retrieves approved healthcare operational guidance while maintaining document lifecycle control, abstention, human review, and auditability.



\---



\# Architecture



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

Grounded Answer / Human Review  

↓  

Audit Record



\---



\# Major Experiments



\## Semantic Retrieval



Result:



\- Top-1: 70%

\- Top-k: 90%



\---



\## BM25



Result:



\- Top-1: 20%

\- Top-k: 40%



Finding:



Exact terminology can help, but BM25 was weaker overall.



\---



\## Hybrid Retrieval



Result:



\- Top-1: 70%

\- Top-k: 90%



Finding:



Hybrid retrieval did not improve aggregate performance over semantic retrieval.



\---



\## RRF-Only



Result:



\- Top-1: 40%

\- Top-k: 50%



Finding:



Removing the existing reranking stage reduced performance.



\---



\# Major Failure



Initial abstention success:



0%



Out-of-scope questions still retrieved plausible operational evidence.



\---



\# Root Cause



Semantic similarity measures closeness of meaning.



It does not prove:



\- the question is allowed;

\- the evidence is sufficient;

\- the document is authoritative;

\- the requested information exists in the corpus.



\---



\# Control Introduced



Deterministic query-scope gate.



Final abstention success:



100%



The semantic retrieval benchmark remained:



\- Top-1: 70%

\- Top-k: 90%



\---



\# Human Review



Current decisions:



\- AUTO\_ANSWER

\- REVIEW\_REQUIRED

\- ABSTAIN



Current 14-case distribution:



\- AUTO\_ANSWER: 3

\- REVIEW\_REQUIRED: 8

\- ABSTAIN: 3



\---



\# Reusable Engineering Principles



1\. Similarity does not equal sufficient evidence.

2\. Relevance does not equal authority.

3\. More complexity does not automatically improve retrieval.

4\. Uncertainty should influence automation level.

5\. Governance controls should be testable.

6\. Human accountability should remain explicit.



\---



\# Current Limitations



\- synthetic corpus;

\- small benchmark;

\- prototype thresholds;

\- no NHS expert validation;

\- no production deployment;

\- no real-world monitoring;

\- no validated clinical use.



\---



\# Future Evolution



This project should evolve into the evidence layer supporting:



Agentic Operational Assistant  

↓  

NHS Sovereign Operational Intelligence \& Evidence Copilot

