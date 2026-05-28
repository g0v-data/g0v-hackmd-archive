## Reviewer 1


We thank the reviewer for their thoughtful feedback on our submission.

With respect to our evaluation, we believe that our experimental scope is extensive, covering 36 model/dataset combinations, many metrics, distribution shifts, selective prediction, and linguistic calibration.  This view was supported by the other reviewers, who characterized our empirical study as "much broader than typical calibration papers" (KUuD) and "broad" and "empirically strong" (BhkZ). 

We appreciate the reviewer's particular concerns, with further questions about the method's capacity to generalize.  In response to these concerns, we have run new experiments, including with a new dataset with a longer free-form answer format that is not amenable to exact matching.  We will add these results to an updated draft.  Please see below for these and other results. 

**Validity of self-consistency calibration**

<!-- **(1) Central premise is validated only implicitly. That SC tracks correctness in reasoning models rests on aggregate ECE in Table 1 plus a citation to Lyu et al. that actually evaluates non-reasoning models. High-confidence-tail behavior, where deployment risk concentrates, isn't analyzed. (Section 4.1, lines 192–202; Section 3, line 109; Section 2, lines 75–78)
Suggestion: Add a reliability diagram for raw Test-Time SC (Figure 3 currently shows only the distilled predictor). Add conditional accuracy among examples with SC ≥ 0.9 and ≥ 0.95. Both should be computable from existing data.** -->

We agree that it is important to validate the underlying premise of our approach, that self-consistency tracks correctness in this setting (we also believe this is a contribution of this work).  Besides Table 1, results for test-time SC are also included in Figure 2, Tables 4+5 (in comparison to base model calibration), and Table 9 (with results by dataset).  We will point to these results more clearly in a revised manuscript.  In general, we find it to be a reliable and sharp confidence signal.

In response to the reviewer's concern, we will add TT-SC to the reliability diagrams in Figure 3 (while we cannot share them here, they have better ECE and also visually appear closer to x=y).  Below, please see the results corresponding to conditional accuracy among examples with SC ≥ 0.9 and ≥ 0.95.  We compare the average accuracy and confidence in these buckets for both our method and TT-SC.  TT-SC enables well-calibrated predictions in these high-confidence ranges.

| Dataset   | Method      |   Threshold |   AvgAcc |   AvgConf |   diff |
|:----------|:------------|------------:|--------------:|----------------:|-------:|
| gsm8k     | Self. cons. |       0.900 |         0.969 |           0.974 | -0.005 |
| gsm8k     | Self. cons. |       0.950 |         0.977 |           0.984 | -0.006 |
| polymath  | Self. cons. |       0.900 |         0.942 |           0.965 | -0.023 |
| polymath  | Self. cons. |       0.950 |         0.959 |           0.981 | -0.022 |
| gsm8k     | Ours        |       0.900 |         0.922 |           0.947 | -0.024 |
| gsm8k     | Ours        |       0.950 |         0.951 |           0.977 | -0.026 |
| polymath  | Ours        |       0.900 |         0.889 |           0.964 | -0.076 |
| polymath  | Ours        |       0.950 |         0.889 |           0.964 | -0.076 |


**Dependence on exact matching**

<!-- **(2) The validated regime is much narrower than the framing suggests. All five datasets share the same structure (short, exact-matchable answers) even though the motivating use cases (tutor hints, triage advice, agentic actions) don't have this structure. The method's reliance on string-equality agreement is invisible in the experiments but central to whether it generalizes. (Section 4, lines 132–145; Section 1, lines 31–42; Appendix A.2)
Suggestion: Either run one end-to-end experiment on a longer-form or non-factoid dataset using embedding-based agreement (e.g., cosine similarity above a threshold) in place of exact match or scope claims to "short-answer generation with exact-matchable references."** -->



We believe that tutor hints, triage advice, agentic actions, are all closely related to math and free-form QA (as these are considered in the calibration literature [1]).  We would like to note that the example queries in Figure 1 are taken directly from the Polymath dataset, which we use in our experiments.  In response to this concern, we provide 2 additional experiments.  We will include these results in a final paper.

We have run 6 models (all Qwen3 models and Nemotron-8B) on the TruthfulQA task, which is a sentence-level task that is not amenable to exact matching.  For semantic matching, we adopt the method of [1], where generations are clustered together based on bi-directional entailment, with a sample size of k=20.  We also use entailment to mark correctness.  The average model accuracy is 40\%, as we observe this task to be difficult for reasoning models.  ECE2 results are below.  Our method outperforms other unsupervised baselines; our worst-case performance is better than the best performance of any other method under comparison.

| Method   |   ECE2 - min |   ECE2- mean |   ECE2 - max |
|:-----------------|------------------:|-------------------:|------------------:|
| Token Probs.     |             0.300 |              0.375 |             0.468 |
| Ans. Probs.      |             0.407 |              0.521 |             0.662 |
| Verbal Conf.     |             0.359 |              0.466 |             0.667 |
| Ours             |             0.117 |              0.205 |             0.242 |


We further study the dependence on exact matching by applying the semantic clustering method to our two existing open-domain QA datasets.  These methods for consistency scoring perform comparably.


| Dataset   | Method       |   ECE1 |   ECE2 |   MCE |   Brier |   AUROC |
|:----------|:-------------|-------:|-------:|------:|--------:|--------:|
| TriviaQA | Sem. Cluster |  0.088 |  0.104 | 0.238 |   0.182 |   0.774 |
| TriviaQA | Ex. Match |  0.080 |  0.095 | 0.211 |   0.184 |   0.760 |
| TriviaQA | Best Unsup. | 0.289 | 0.322 | 0.500 | 0.304 | 0.701 |
| WebQ      | Sem. Cluster |  0.121 |  0.141 | 0.285 |   0.228 |   0.657 |
| WebQ      | Ex. Match |  0.106 |  0.126 | 0.273 |   0.230 |   0.624 | 
| WebQ      | Best Unsup. | 0.399 | 0.409 | 0.537 | 0.386 | 0.604 |


[1] Semantic Uncertainty: Linguistic Invariances for Uncertainty Estimation in Natural Language Generation https://arxiv.org/abs/2302.09664

<!-- **(3) Distribution-shift experiments are too mild to support the deployment claim, and the cost story depends on it. Shifts are within task families; motivating scenarios involve much larger ones. If the predictor doesn't transfer broadly, the offline cost (~100k generations per setup) recurs whenever the deployment shifts, undermining the "lightweight at deployment" framing. (Section 4.2, lines 259–280; Section 4, line 146; Section 5, lines 335–340)
Suggestion: Run at least one cross-task-family transfer experiment (math → code, factoid QA → multi-step reasoning), or analyze what features the calibrator is responding to (representational geometry vs. surface task features) so readers can reason about how often recalibration would be needed in practice.** -->

**Further distribution shifts**

In response to this concern, we have run an additional distribution shift experiment, to compliment the shifts across domains and languages.  Here, the model is trained on a Science QA task, and deployed to a heterogeneous distribution that mixes open-domain QA (TriviaQA) with math (as this seems more natural than a situation where 100\% of the test data is from an entirely different task family); 20% of the queries are from the math domain (we separately test with both GSM8K and polymath). In this case, the model faces distribution shifts across domains, tasks, and in the case of PolyMath, languages.

Results are shown in the table below; our method outperforms other unsupervised baselines.  

| Math source   | Method       |   ECE2 |   Brier |
|:--------------|:-------------|-------:|--------:|
| GSM8K         | Ans. Probs.  |  0.336 |   0.319 |
| GSM8K         | Token Probs. |  0.242 |   0.233 |
| GSM8K         | Verbal Conf. |  0.279 |   0.281 |
| GSM8K         | Ours         |  0.089 |   0.215 |
| Polymath      | Ans. Probs.  |  0.336 |   0.320 |
| Polymath      | Token Probs. |  0.242 |   0.234 |
| Polymath      | Verbal Conf. |  0.279 |   0.281 |
| Polymath      | Ours         |  0.121 |   0.226 |

With respect to offline cost, we note that our method does not require 100k generations in any of our experiments.  The most we use is 40k, but Table 12 also shows we can reduce ECE by over 50\% against baselines with just 2k.  To further address these concerns around data gathering and sample cost, we have re-run experiments with fewer training examples (100, 200) and number of samples (10, 20); our method remains effective with as few as 1k generations. 

|   Train Ex. |   Samples | Method            |   ECE2 |   Brier |
|-----------:|-----------:|:------------------|-------:|--------:|
|        100 |         10 | Ours              | 0.0906 |  0.1642 |
|        100 |         20 | Ours              | 0.0900 |  0.1632 |
|        200 |         10 | Ours              | 0.0863 |  0.1598 |
|        200 |         20 | Ours              | 0.0849 |  0.1583 |
|        - |        - | Best Unsup. | 0.2155 |  0.2214 |


We will include both of these experiments in a final paper.

<!-- **(4) The linguistic-calibration experiment is missing a control that may substantially weaken its headline. The method is compared only against miscalibrated baselines, leaving open whether the win is "this signal is uniquely useful" or just "any well-calibrated signal helps." (Section 4.3, lines 316–333; Table 16)
Suggestion: Add a Test-Time SC condition to the experiment, since Table 1 shows it's similarly calibrated to the distilled method. If downstream performance is comparable, reframe the contribution as "we deliver well-calibrated signals cheaply" rather than "our confidence estimates are uniquely useful."** -->

**Test-time SC and linguistic calibration**

We have closely re-read this passage, and are unsure the headline the reviewer is referring to; no statements read or paraphrase as "this signal is uniquely useful". We also would not argue that other well-calibrated signals would not also be helpful, as this is the central idea of linguistic calibration.  We state the basis of our comparison in lines 323-325, which is the same set of unsupervised baselines that we use through the paper.   

For completeness, we have run a test-time self-consistency baseline. Please see below for results averaged across models.  This signal also improves the decision-maker's calibration, as compared to the more uncalibrated baselines.  We will include these results in our final paper.


| Method       |    Acc |   ECE2 |    MCE |   Brier |
|:-------------|-------:|-------:|-------:|--------:|
| Base Model   | 0.6860 | 0.2749 | 0.3721 |  0.2608 |
| Token Probs. | 0.6561 | 0.2149 | 0.4095 |  0.2483 |
| Verbal Conf. | 0.6467 | 0.3180 | 0.4886 |  0.3097 |
| Ours         | 0.6538 | 0.1279 | 0.2446 |  0.2175 |
| TT-SC        | 0.6548 | 0.1440 | 0.2409 |  0.2168 |



## Reviewer 2

We thank the reviewer for taking the time to consider our submission.  Please see below for our responses to your individual concerns.

**Paper contribution**

<!-- **Limited methodological novelty. The components are familiar: self-consistency as a confidence signal, offline distillation, embedding probes, and isotonic regression. The main contribution is their composition plus a strong empirical study. The paper should avoid overselling the method as algorithmically novel.** -->

We do not claim algorithmic novelty in the individual components; our contribution is the conceptual choice of treating repeated sampling as an offline, unlabeled supervision source for the single-generation regime, together with the empirical demonstration that this works broadly. If there is any particular wording the reviewer feels should be revised, we are happy to do so; we will make a pass through the introduction and method section to ensure the contribution is framed as the composition and the regime it unlocks rather than the parts.

We would also argue that simplicity here is a strength: a lightweight, off-the-shelf pipeline is what makes the approach deployable in the constrained settings we target, and it is consistent with how much influential calibration work has been valued (see response to Reviewer viF2).


**Matched supervised baseline**

<!-- **The supervised comparison is weak. The supervised baseline is Platt scaling on token probabilities. A more informative comparison would train the same embedding-plus-isotonic predictor on true correctness labels. Without this, it is hard to separate the value of self-consistency targets from the value of the predictor architecture.** -->

We thank the reviewer for this suggestion, and agree that this is a useful ablation that we will include in the paper.  Please see below for results including this baseline in all experiments.

| Method     |   ECE1 |   ECE2 |    MCE |   Brier |   AUROC |
|:-----------|-------:|-------:|-------:|--------:|--------:|
| Ours       | 0.0696 | 0.0864 | 0.2013 |  0.1550 |  0.7080 |
| Emb. + Iso. Reg.  | 0.0519 | 0.0666 | 0.1755 |  0.1513 |  0.7103 |
| (Current) Supervised | 0.0524 | 0.0649 | 0.1319 |  0.1604 |  0.6524 |

As expected, including the ground-truth labels meaningfully improve ECE over our unsupervised method.  The effects on sharpness (Brier and AUROC) are less significant.  Compared to our original supervised baseline, ECE is comparable; AUROC in particular improves, which makes sense given the more expressive input (embeddings vs. token probs).


**Self-consistency failures and WebQ performance**

<!-- **Self-consistency failures are not diagnosed enough. WebQ appears much weaker than the math datasets, likely because semantically equivalent answers can have different surface forms. The paper notes this issue but does not analyze where or why the self-consistency target breaks down. 
On WebQ, how much of the self-consistency failure comes from correct answers expressed with different surface forms? Did semantic answer clustering improve the target?** -->


We thank the reviewer for the question. In rsponse to this concern, we ran a new experiment: we produced the WebQ self-consistency targets using semantic answer clustering rather than exact matching, and found it yields comparable calibration.


| Method                      |   ECE1 |   ECE2 |   MCE |   Brier |   AUROC |
|:----------------------------|-------:|-------:|------:|--------:|--------:|
| Ex. Matching |  0.106 |  0.126 | 0.273 |   0.230 |   0.624 |
| Sem. Cluster |  0.121 |  0.141 | 0.285 |   0.228 |   0.657 |
| Best Unsup.  |  0.399 |  0.409 | 0.537 |   0.386 |   0.604 |


Clustering slightly improves AUROC and Brier but slightly worsens ECE, and both far exceed the best unsupervised baseline. This suggests surface-form variation is not the primary driver of WebQ's weaker numbers. We will add this comparison to the paper.

To explain WebQ performance, we note that it is the lowest-accuracy dataset for every model (Table 6), and its weaker calibration fits the accuracy–calibration trend in Figure 4.  Its answer format also matches TriviaQA (short answers with a set of accepted matches), so format alone does not explain the gap.

Finally, on diagnosing individual failures: because calibration is defined over sets of predictions, it is inherently hard to attribute to specific examples. A model that reports 95% confidence on 100 items and is correct on 99 is well-calibrated, but it is not meaningful to flag the one potential "error" (high-consistency-but-wrong case), which in this case helps calibration rather than hurt it.


**Offline costs**

<!-- **Offline cost is understated. The method requires many offline generations per model and target distribution. This may be reasonable for some local deployments, but in black-box API settings it can be costly and may need to be repeated after domain shifts or model updates. The paper should report token counts or approximate API cost.  
-How does performance scale with the number of unlabeled calibration examples, not only with the number of self-consistency samples per example?
-What is the approximate offline calibration cost in tokens, wall-clock time, or API dollars for a representative black-box model?** -->


We thank the reviewer for raising the cost question; we have added the requested experiments here, and will include them with a more extensive discussion about offline cost in a final paper.

First, we re-ran our method varying both the number of training examples (100, 200) and samples per example (10, 20). The method remains effective with as few as ~1,000 total generations (e.g., 100 examples × 10 samples), far outperforming the best unsupervised baseline:


|   train_ex |   k_ablate | Method            |   ECE2 |   Brier |
|-----------:|-----------:|:------------------|-------:|--------:|
|        100 |         10 | Ours              | 0.0906 |  0.1642 |
|        100 |         20 | Ours              | 0.0900 |  0.1632 |
|        200 |         10 | Ours              | 0.0863 |  0.1598 |
|        200 |         20 | Ours              | 0.0849 |  0.1583 |
|        - |        - | best unsupervised | 0.2155 |  0.2214 |


This complements our existing per-example sample ablation (Table 12) by showing the method is also robust to a small calibration set, which directly bounds the offline cost.

This table estimates the cost of running 1,000 representative math benchmark questions through public model APIs, assuming roughly 250 input tokens and 750 output tokens per question to include both reasoning/explanation and a final answer. Costs are computed from publicly listed per-token API prices, with batch/flex discounts included where available.


| model                              |      cost |
| ---------------------------------- | --------: |
| Gemini 2.5 Flash-Lite  | **$0.16** |
| Gemini 2.5 Flash       | **$0.98** |
| Gemini 3 Flash Preview | **$1.19** |
| GPT-5.4 mini              | **$1.78** |
| Gemini 2.5 Pro         | **$3.91** |
| Claude Haiku 4.5                   | **$4.00** |

For open weights, running k=10 with n=100 on GSM8K with a single A100 under vLLM takes ~6 min for Qwen3-1.7B and ~13 min for Qwen3-8B. We will add these figures to the appendix.

**Robustness to deployment decoding**

<!-- **Robustness to deployment decoding is incomplete. Training-temperature ablations are useful, but the more practical question is what happens when the deployed model uses a different test-time temperature or greedy decoding. How robust is the predictor when trained at one decoding temperature but deployed with another, especially greedy or low-temperature decoding?** -->

We thank the reviewer, and we may not have made this clear enough in the paper: all of our main experiments already use a train/test temperature mismatch. Calibration targets are sampled at temperature 0.7 (with ablations at 0.5 and 0.9, Figures 13–14), while test-time decoding uses 0.6. The strong results throughout therefore already reflect a predictor trained at one decoding temperature and deployed at another, and the temperature ablations show robustness across the sampling settings we vary. We will state this train/test gap explicitly.

On greedy and very-low-temperature decoding: we focus on 0.6 at test time because this is the official Qwen3 recommendation for its thinking mode, which explicitly advises against greedy decoding, noting it can cause performance degradation and repetition loops. Since the reasoning models we study are not intended to be deployed greedily, calibrating for a decoding regime the model maker discourages would not reflect the realistic deployment that this paper aims to focus on. That said, we agree the broader sensitivity to test-time decoding is a reasonable question and will note it as a direction for future work.




## Reviewer 3


We thank the reviewer for the careful read and for recognizing that the paper offers an effective, empirically strong solution to an important and practical problem, validated across model families, math and QA datasets, distribution shift, black-box embeddings, sample-size ablations, and two downstream decision-making settings. We address the two concerns raised below.


**The main idea feels like a straightforward way to train a cheap model to imitate repeated sampling
My main concern is low novelty. The paper’s core method is to compute self-consistency from repeated offline samples and train a small predictor to approximate that signal at test time. This feels like a direct distillation of test-time self-consistency rather than a new idea. Overall I view the paper as useful but incremental.**


We thank the reviewer, but we want to push back directly on the novelty assessment. We believe that the simplicity of our method is one of our primary contributions. Our target deployments (e.g. mobile health, workplace assistants, tutoring) share three constraints that jointly rule out much of the calibration literature: scarce labels, real-time inference budgets, and a need for reliable uncertainty estimates. Identifying self-consistency as the right target to distill, a choice that satisfies all three properties where no existing method does, is a non-obvious and carefully picked choice we made from a combinatorially large design space of possible calibration methods. Instead of proposing overcomplicated pipelines that are impressive in appearance, but are often fragile and fail to generalize in practice, we present a fundamental contribution that fills a crucial gap in the literature.  The simplicity of our method enables strong generalization in a new deployment regime: across extensive experiments including 9 models, 5 datasets, distribution shift, and black-box access, our method shows consistently strong performance across all metrics. Our focus is a simple, empirically sound method that crisply solves the problem rather than a complicated one that embellishes, and we hope the reviewer will reconsider the novelty assessment in this light.

We also argue that this is how influential work in LLM calibration has consistently been valued. 
 - Tian et al. [1] show that simply prompting a model to state its confidence in words yields better calibration than its token probabilities.
 - Kuhn et al. [2] cluster generations by bi-directional entailment rather than exact matching.
 - Damani et al. [3] obtain calibrated uncertainty by adding a Brier-score term to the RLVR reward. 
 - Luo et al. [4], whose setting most directly relates to ours, recalibrate an overconfident post-trained model using its corresponding base model token probs. 

None of these rests on algorithmic complexity; instead, each is a conceptual choice about the right signal, equivalence, or objective, yet the field has rightly recognized them as substantial contributions. We see our work as fitting in this tradition: the difficulty and the novelty lie in identifying repeated sampling as an offline supervision source for the underserved single-generation, unlabeled regime, not in the complexity of the predictor that distills it.

- [1] Just Ask for Calibration: Strategies for Eliciting Calibrated Confidence Scores from Language Models Fine-Tuned with Human Feedback (https://arxiv.org/abs/2305.14975), EMNLP 2023
- [2] Semantic Uncertainty: Linguistic Invariances for Uncertainty Estimation in Natural Language Generation (https://arxiv.org/abs/2302.09664), ICLR 2023
- [3] Beyond Binary Rewards: Training LMs to Reason About Their Uncertainty (https://arxiv.org/abs/2507.16806), ICLR 2026
- [4] Your Pre-trained LLM is Secretly an Unsupervised Confidence Calibrator (https://arxiv.org/abs/2505.16690), Neurips 2025


**I am also not fully convinced that the method learns confidence for the specific generated answer, since the question-only ablation is very strong and sometimes close to or better than the full response-based predictor. This suggests that much of the gain may come from learning question difficulty.**


It is correct that the question-only and full predictors achieve similar marginal calibration. This is expected: both are trained against the same self-consistency targets, and ECE rewards marginal calibration, which a difficulty estimate largely captures on its own (as we note in Section 4.1, a predictor near the base accuracy rate can already score well on ECE). 

The important question is whether the full predictor extracts answer-specific information beyond question difficulty, and on the discriminative metrics the two separate clearly.  Because the question-only predictor never observes the generated answer, it must assign the same confidence to every response to a given question—including cases where the model produces an incorrect answer to an otherwise easy question. The full predictor, conditioned on the actual response, can down-weight such cases. This is exactly why it separates correct from incorrect answers better: across all five datasets (Table 9), AUROC increases strictly and monotonically from question-only → our full method → test-time self-consistency, with Brier score following the same ordering (except for Brier score on WebQ). The progression is the cleanest summary of the effect: all three are well-calibrated marginally, but the stronger, answer-aware methods are sharper. This carries directly into decisions: in selective prediction (Figure 6), the question-only ablation underperforms the full method, precisely because weaker ranking yields weaker abstention.

Finally, we would also note that estimating model-dependent difficulty without any labels is itself non-trivial, and is arguably not distinct from confidence calibration.  A natural way for any predictor (or person) to express the difficulty of a problem is precisely its estimated probability of answering correctly. That said, our results show the full method goes beyond this, capturing answer-level signal that measurably improves both discrimination and downstream decisions.
