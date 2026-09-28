# Week 19 Large Benchmark Design

## Historical status

This is the original Week 19 expansion design, written after the 38-case Hybrid Rescue experiment and before the 75-case evaluation set was implemented. The expansion is now complete. The design requirements below are preserved as research history, not a claim that every proposed metric, category quota or review outcome was implemented and measured.

The final Week 19 record reports 338 regression tests passed and Hybrid Rescue at 82.22% Top-1 and 82.22% Top-k on the controlled 75-case benchmark. Later work added claim-level sufficiency, citation verification, high-risk protection, guarded semantic rescue, and Day 6 evidence-set relationship / corrective false-premise validation. See [CURRENT_STATUS.md](../CURRENT_STATUS.md) for the authoritative progress record: Week 19 and Week 20 Day 1 are complete; Week 20 Day 2 is next.

## Original objective

Expand the controlled benchmark from 38 to approximately 75 cases to test whether experimental Hybrid Rescue continues to outperform the original Hybrid baseline as questions become harder and more diverse. This is a research benchmark, not production NHS validation.

## Historical 38-Case Baseline

Reported results on the 38-case benchmark at the time of this design:

| Method | Top-1 | Top-k | Abstention | Active-only |
| --- | --- | --- | --- | --- |
| Semantic | 75.0% | 87.5% | 100% | 100% |
| Keyword | 41.7% | 62.5% | 100% | 100% |
| Hybrid | 75.0% | 87.5% | 100% | 100% |
| RRF-only | 70.8% | 75.0% | 100% | 100% |
| Hybrid Rescue | 79.2% | 91.7% | 100% | 100% |

Hybrid Rescue was the best experimental method on these measured metrics at this milestone. The small evaluation set does not establish general superiority.

## Proposed 75-Case Distribution

Counts describe the proposed final benchmark, not 75 additional cases. These are design quotas, not a verified breakdown of the implemented 75 cases. Retain the existing 38 cases as a regression set and add approximately 37. Assign one primary category per case for counting; secondary tags can overlap. Reconcile existing cases against these quotas before authoring new ones, documenting any redistribution while retaining the 75-case target.

| Category | Cases | Purpose and failure mode | Expected behaviour | Main controls tested |
| --- | ---: | --- | --- | --- |
| Clear single-document operational questions | 8 | Establish basic competence; detect ranking regressions on direct questions. | Retrieve the authoritative answer-bearing document and retain adequate evidence. | Retrieval |
| Hard paraphrases | 7 | Test indirect wording; detect dependence on exact titles or concept phrases. | Recover the intended topic without unnecessary abstention. | Retrieval; evidence sufficiency |
| Ambiguous operational questions | 4 | Test underspecified intent; detect unjustified selection of one interpretation. | Request clarification or route to review rather than automatically answer. | Review governance; evidence sufficiency |
| Cross-document questions | 8 | Test questions needing two or more sources; detect incomplete evidence sets. | Cover every required subject within final_k; rescue missing evidence or abstain if coverage remains incomplete. | Retrieval; evidence sufficiency |
| Lifecycle conflicts | 5 | Test Active versus Draft/Superseded/Archived versions; detect obsolete authority winning on relevance. | Use eligible Active evidence only; abstain if no adequate eligible source exists. | Lifecycle control |
| In-scope but no-evidence questions | 6 | Test absent operational subjects; detect plausible but unsupported answers. | Remain IN_SCOPE and abstain for missing evidence, including after rescue. | Evidence sufficiency |
| Clinical out-of-scope questions | 4 | Test treatment/prescribing requests, including operational wording; detect clinical leakage. | Block at the scope gate before retrieval. | Scope |
| Current/external-information questions | 4 | Test live information needs; detect stale corpus content used as current fact. | Block unsupported live/external requests while distinguishing local-policy wording such as current escalation process. | Scope |
| Adversarial prompts | 5 | Test attempts to bypass controls; detect unsafe instruction following. | Reject the bypass instruction and preserve scope, evidence, and lifecycle controls; process a safe underlying request only when justified. | Scope; lifecycle control; review governance |
| Near-duplicate policy questions | 3 | Test similar wording across distinct policies; detect the wrong population, service, or version being selected. | Select the applicable authoritative policy; review unresolved ambiguity. | Retrieval; lifecycle control |
| Conflicting-document questions | 4 | Test incompatible statements in eligible sources; detect silent cherry-picking. | Surface the conflict and route to review; do not automatically resolve unsupported contradictions. | Evidence sufficiency; review governance |
| Partial-evidence questions | 5 | Test requests where only some required evidence exists; detect partial coverage treated as complete. | Rescue the missing component if available; otherwise abstain from a complete answer. | Evidence sufficiency; retrieval |
| Multi-hop operational questions | 4 | Test evidence chains linking conditions, responsibilities, and actions; detect unsupported intermediate steps. | Retrieve support for every required link and route unresolved reasoning to review. | Retrieval; evidence sufficiency; review governance |
| Lexical mismatch questions | 4 | Test acronyms, synonyms, and alternate terminology; detect vocabulary dependence across methods. | Recover equivalent concepts without broadening scope or accepting unrelated evidence. | Retrieval; evidence sufficiency |
| Retrieval distractor questions | 4 | Test highly similar but non-answering documents; detect relevance mistaken for support. | Prefer evidence that actually supports the question and reject distractor-only sets. | Retrieval; evidence sufficiency |
| **Total** | **75** | | | |

## Case Design and Ground Truth

Each case should record its ID, primary category, secondary tags, question, expected scope, corpus answerability, required concepts, acceptable document/chunk IDs, required evidence groups, lifecycle constraints, and expected outcome: answer, review/clarification, or abstain. Record the rationale and any evidence explicitly absent from the corpus.

Distinguish absent evidence from evidence that exists but retrieval misses. For cross-document and multi-hop cases, define the complete required evidence set; retrieving any one acceptable document is not complete coverage. Ensure answerable cases can fit within the fixed final_k, or label capacity-limit stress cases separately.

Near-duplicate and conflicting-document cases need suitable corpus fixtures. If those fixtures do not exist, mark the cases as pending fixture design rather than inventing ground truth. No corpus or case changes are made by this document.

Keep current cases identifiable and freeze new expected outcomes before comparative runs. Include unseen paraphrases and negative controls. Report the original 38-case regression slice and new-case slice separately; avoid treating paraphrase variants as independent evidence of broad generalisation.

## Proposed Metrics

These are proposed definitions, not confirmation that the runner reports every metric. In particular, the complete-evidence Top-k definition below must not be assumed to underlie the final reported 82.22% without verifying the scoring implementation. The 38-case and 75-case results are not directly comparable without accounting for case-set and metric differences.

Report numerators, denominators, and category breakdowns alongside percentages. Use N/A where no cases qualify. Preserve existing metrics for comparison and label stricter new metrics separately.

| Metric | Definition |
| --- | --- |
| Top-1 accuracy | Among answerable cases with a defined acceptable first result, proportion whose first scored result is acceptable. Abstentions count as failures in this denominator. |
| Top-k coverage | Among answerable cases with defined evidence requirements, proportion whose first k scored results cover all required evidence groups. Report legacy any-hit Top-k separately if its definition differs. |
| Abstention success | Among cases explicitly labelled unanswerable, proportion producing abstention. Report scope-blocked and in-scope unsupported cases separately. |
| Active-only compliance | Proportion of evaluated cases with no ineligible result in the final evidence set. Also report eligible-result counts among nonempty outputs so empty sets do not conceal lifecycle failures. |
| False AUTO_ANSWER rate | Among AUTO_ANSWER decisions, proportion whose reference outcome requires review/clarification or abstention, or whose evidence is inadequate. Report unsafe automatic-answer counts by category. |
| False abstention rate | Among answerable cases with adequate eligible evidence available in the corpus, proportion incorrectly abstaining. Distinguish retrieval misses from scope or evidence-check errors. |
| Rescue activation rate | Among in-scope cases evaluated by Hybrid Rescue, proportion that invoke the rescue path. |
| Rescue success rate | Among rescue attempts, proportion that finish with adequate evidence according to the reference requirements, not merely the checker reporting SUFFICIENT. |
| Rescue regression rate | Among previously correct original-Hybrid cases, proportion that Hybrid Rescue makes incorrect under the same reference scoring. Report affected case IDs and lost evidence. |
| Multi-document coverage | Among answerable cases requiring multiple documents, proportion covering every required source/evidence group within final_k. |
| Lifecycle conflict accuracy | Among lifecycle-conflict cases, proportion making the correct authority selection or abstaining when adequate eligible evidence is absent. |
| Adversarial rejection accuracy | Among adversarial cases, proportion rejecting the prohibited instruction while preserving the expected safe handling of any underlying request. Blanket refusal is not automatically correct. |
| No-evidence abstention accuracy | Among in-scope cases whose required evidence is absent from the corpus, proportion abstaining for insufficient evidence. Scope misclassification is not counted as correct layer behaviour. |

Review-governance metrics require recorded review decisions. If the runner does not produce them, report them as not measured rather than inferring AUTO_ANSWER from retrieval success. Concept coverage alone cannot establish entailment, contradiction handling, or multi-hop correctness; these need explicit reference checks or review.

## Promotion Criteria for Hybrid Rescue

Do not promote Hybrid Rescue to default unless it:

- Maintains or improves Top-1 versus original Hybrid on the same cases.
- Maintains or improves Top-k versus original Hybrid using the same metric definition.
- Maintains 100% abstention on explicitly unanswerable test cases.
- Maintains 100% Active-only lifecycle compliance.
- Does not materially regress previously correct Hybrid cases; inspect paired case-level regressions and their severity.
- Keeps false AUTO_ANSWER acceptably low under a documented research review policy agreed before examining results.
- Shows stable performance across several categories, rather than improvement driven by one or two rescued cases.

Define material regression and acceptable false AUTO_ANSWER with reviewers before the experiment; do not invent a production threshold. Report uncertainty and small category denominators. Passing these criteria supports further research evaluation, not production readiness or NHS safety certification.

## Experiment Discipline

- Do not tune retrieval against individual cases without checking full-benchmark regression.
- Preserve baseline results, including corpus, case-set, code, and configuration versions.
- Isolate each experimental change; use identical corpus, thresholds, and final_k for paired method comparisons.
- Record failed experiments and the reasons for rejecting them.
- Distinguish retrieval failure from scope failure and evidence-sufficiency failure; record lifecycle and review-governance failures separately.
- Preserve raw retrieval, pre/post-rescue evidence, decisions, and audit records. Do not overwrite earlier benchmark outputs.

## Original Next Implementation Step — Subsequently Completed

The next step recorded at the time was: create the new benchmark cases without changing retrieval logic. The evaluation set subsequently expanded to 75 cases. This does not establish that all proposed category quotas or metrics were implemented. Current next work is recorded in [CURRENT_STATUS.md](../CURRENT_STATUS.md).
