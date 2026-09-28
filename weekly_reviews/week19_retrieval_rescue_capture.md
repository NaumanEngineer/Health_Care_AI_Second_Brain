# Week 19 — Governed Retrieval Rescue

## Historical status

This capture records the earlier Week 19 **38-case retrieval-rescue experiment**, not the final Week 19 architecture or results. Its benchmark figures and test counts are preserved as milestone evidence.

Week 19 later reached 75 retrieval cases, 82.22% Hybrid Rescue Top-1 and Top-k, and 338 passing regression tests. Subsequent work added claim-level sufficiency, citation verification, high-risk claim protection, guarded semantic rescue, and Day 6 evidence-set relationship / corrective false-premise validation. The citation benchmark recorded 14/15 correct (93.3%), zero false acceptances and one false rejection before the Day 6 work addressed the CIT010 class of problem; that does not establish a new end-to-end citation score.

See [CURRENT_STATUS.md](../CURRENT_STATUS.md) for current progress and the tested Architecture v1 baseline. Week 19 and Week 20 Day 1 are complete; Week 20 Day 2 is next. Results from the 38-case and 75-case stages should not be interpreted as a direct performance change without accounting for the case sets and scoring definitions.

## Capture

The completed experiment used a 38-case governed benchmark to separate retrieval quality from evidence-based abstention.

- Scope gate and evidence sufficiency are separate safety layers.
- The scope gate handles disallowed questions.
- Evidence sufficiency handles in-scope questions where the corpus lacks adequate support.
- Simple similarity thresholds were rejected because supported and unsupported cases had overlapping scores.
- A deterministic, concept-first evidence-sufficiency layer was introduced.
- Q029 cybersecurity, Q030 electronic patient record (EPR) failure, and Q031 oxygen supply correctly abstain because specific evidence is absent.
- Q027 exposed a multi-document retrieval weakness: answering required both severe-weather and ambulance-handover evidence.

### Failed experiment: global RRF-first reranking

Global RRF-first hybrid reranking fixed Q027 but reduced overall Hybrid performance:

- Top-1: 75.0% → 70.8%.
- Top-k: 87.5% → 75.0%.

The global change displaced useful semantic ordering. It was rejected, and the original hybrid ranking path was restored.

### Successful experiment: targeted hybrid evidence rescue

- Preserve normal hybrid retrieval when evidence is sufficient.
- Invoke RRF/BM25 rescue only when evidence coverage is incomplete.
- Q027 initially lacked `severe_weather` evidence.
- Rescue recovered DOC-009 Severe Weather Operational Plan.
- Final evidence became SUFFICIENT.

Hybrid Rescue remains a separate experimental method, rather than the default retrieval strategy.

### Final Results of the 38-Case Rescue Experiment

| Method | Top-1 | Top-k | Abstention | Active-only |
| --- | --- | --- | --- | --- |
| Semantic | 75.0% | 87.5% | 100% | 100% |
| Keyword | 41.7% | 62.5% | 100% | 100% |
| Hybrid | 75.0% | 87.5% | 100% | 100% |
| RRF-only | 70.8% | 75.0% | 100% | 100% |
| Hybrid Rescue | 79.2% | 91.7% | 100% | 100% |

These supplied experiment results apply to the controlled synthetic benchmark. The 100% figures describe the measured abstention and lifecycle checks, not a general guarantee of safety.

### Validation at This Milestone

- 11 focused rescue tests passed.
- 270 full tests passed before integration.
- 272 tests passed after benchmark integration.

## Connect

1. **NHS safety:** The system should not answer just because it finds vaguely related operational documents. Missing specific evidence should trigger abstention and appropriate review.
2. **RAG engineering:** Retrieval quality and answer safety are different problems. A relevant result may still fail to support the requested subject or every part of a multi-topic question.
3. **Multi-agent and future agentic systems:** Future agents should verify evidence before acting. An alternate retrieval path can help recover missing support, but must not bypass the evidence gate.
4. **Sovereign NHS Operational Copilot:** The same separation of responsibilities can later support scope control, evidence verification, human review, and safe action gating. This experiment provides a prototype pattern, not validation of that future system.
5. **Second Brain principle:** Failed experiments are useful knowledge, not wasted work. The global RRF regression established why targeted rescue was preferable to replacing the ranking strategy for every query.

## Critique

- The corpus is synthetic.
- This experiment evaluated only 38 cases; the later Week 19 set contains 75.
- The deterministic concept vocabulary requires maintenance.
- Evidence coverage does not prove factual entailment.
- No NHS subject-matter expert has validated the system.
- Rescue remains experimental.
- There is no production monitoring or deployment.

The decision at this milestone was not to promote Hybrid Rescue to default based only on the 38-case benchmark, and to test the improvement on a larger, more representative set. The subsequent expansion to 75 synthetic cases addressed benchmark size; it did not establish production readiness or NHS operational representativeness.

## Compress

1. Scope and evidence sufficiency are different safety problems.
2. Similarity score alone is not a safe abstention rule.
3. Global ranking changes can solve one case while causing wider regressions.
4. Conditional evidence rescue can outperform permanent strategy replacement.
5. Safety improvements must be measured against retrieval quality, not evaluated in isolation.

## Interview Evidence

**Situation:** A multi-document NHS operational question asked how severe-weather pressure and ambulance-handover disruption should be considered together. The initial hybrid results lacked complete evidence.

**Task:** Improve retrieval without weakening abstention or lifecycle safety, or degrading strong baseline retrieval behaviour.

**Action:** I diagnosed semantic, BM25, and RRF behaviour. I rejected similarity-only thresholding because supported and unsupported cases overlapped, and rejected global RRF reranking after it caused wider regressions. I built deterministic concept-first evidence sufficiency and targeted rescue that retained sufficient hybrid results and recovered missing evidence only when needed.

**Result:** Hybrid Rescue achieved 79.2% Top-1, 91.7% Top-k, 100% abstention success, and 100% Active-only compliance on the 38-case synthetic benchmark. Q027 recovered DOC-009 and passed the evidence-sufficiency check.

These are prototype benchmark results, not production NHS performance.
