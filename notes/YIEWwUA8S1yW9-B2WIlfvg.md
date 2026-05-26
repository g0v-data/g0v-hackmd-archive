## Reviewer 1


**My concerns are about the gap between what's claimed and what's tested and whether this method generalizes enough.**



With respect to whether our evaluation, we believe that our experimental scope is extensive, covering 36 model/dataset combinations, many metrics, distribution shifts, selective prediction, and linguistic calibration.  We believe this view was supported by the other reviewers, who characterized our empirical study as "much broader than typical calibration papers" (KUuD) and "broad" and "empirically strong" (BhkZ). 

We appreciate the reviewer's particular concerns, with further questions about the method's capacity to generalize.  In response to these concerns, we have run new experiments, including with a new dataset with a longer free-form answer format that is not amenable to exact matching.  Please see below for these and other results. 


**(1) Central premise is validated only implicitly. That SC tracks correctness in reasoning models rests on aggregate ECE in Table 1 plus a citation to Lyu et al. that actually evaluates non-reasoning models. High-confidence-tail behavior, where deployment risk concentrates, isn't analyzed. (Section 4.1, lines 192–202; Section 3, line 109; Section 2, lines 75–78)
Suggestion: Add a reliability diagram for raw Test-Time SC (Figure 3 currently shows only the distilled predictor). Add conditional accuracy among examples with SC ≥ 0.9 and ≥ 0.95. Both should be computable from existing data.**

We agree that it is important to validate the underlying premise of our approach, that self-consistency tracks correctness in this setting (we also believe this is a contribution of this work).  Besides Table 1, results for test-time SC are also included in Figure 2, Tables 4+5 (in comparison to base model calibration), and Table 9 (with results by dataset).  We will point to these results more clearly in a revised manuscript.  In general, we find it to be a reliable and sharp confidence signal.

In response to the reviewer's concern, we will add TT-SC to the reliability diagrams in Figure 3.  Below, please see the results corresponding to conditional accuracy among examples with SC ≥ 0.9 and ≥ 0.95.  We compare the average accuracy and confidence in these buckets for both our method and TT-SC.  TT-SC enables well-calibrated predictions in these high-confidence ranges.

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



**(2) The validated regime is much narrower than the framing suggests. All five datasets share the same structure (short, exact-matchable answers) even though the motivating use cases (tutor hints, triage advice, agentic actions) don't have this structure. The method's reliance on string-equality agreement is invisible in the experiments but central to whether it generalizes. (Section 4, lines 132–145; Section 1, lines 31–42; Appendix A.2)
Suggestion: Either run one end-to-end experiment on a longer-form or non-factoid dataset using embedding-based agreement (e.g., cosine similarity above a threshold) in place of exact match or scope claims to "short-answer generation with exact-matchable references."**

We believe that tutor hints, triage advice, agentic actions, are all closely related to math and free-form QA (as these are considered in the calibration literature[1]).  We would like to note that the example queries in Figure 1 are taken directly from the Polymath dataset, which we use in our experiments.  

In response to this concern, we provide 2 additional experiments.  We will include these results in a final paper.

We have run 6 models (all Qwen3 models and Nemotron-8B) on the TruthfulQA task, which is a sentence-level task that is not amenable to exact matching.  For semantic matching, we adopt the method of [1], where generations are clustered together based on bi-directional entailment, with a sample size of k=20.  We also use entailment to mark correctness.  The average model accuracy is 40\%, as we observe this task to be difficult for reasoning models.

Our method far outperforms other unsupervised baselines; our worst-case performance is better than the best performance of any other method under comparison.

| Method   |   ECE2 - min |   ECE2- mean |   ECE2 - max |
|:-----------------|------------------:|-------------------:|------------------:|
| Token Probs.     |             0.300 |              0.375 |             0.468 |
| Ans. Probs.      |             0.407 |              0.521 |             0.662 |
| Verbal Conf.     |             0.359 |              0.466 |             0.667 |
| Ours             |             0.117 |              0.205 |             0.242 |

**also add results showing other datasets work without exact match**

We further study the dependence on exact matching by applying the semantic clustering method to our two existing open-domain QA datasets.  These methods for consistency scoring perform comparably, and both far outperform all unsupervised baselines.


| Dataset   | Method       |   ECE1 |   ECE2 |   MCE |   Brier |   AUROC |
|:----------|:-------------|-------:|-------:|------:|--------:|--------:|
| TriviaQA | Sem. Cluster |  0.088 |  0.104 | 0.238 |   0.182 |   0.774 |
| TriviaQA | Ex. Match |  0.080 |  0.095 | 0.211 |   0.184 |   0.760 |
| TriviaQA | Best Unsup. | 0.289 | 0.322 | 0.500 | 0.304 | 0.701 |
| WebQ      | Sem. Cluster |  0.121 |  0.141 | 0.285 |   0.228 |   0.657 |
| WebQ      | Ex. Match |  0.106 |  0.126 | 0.273 |   0.230 |   0.624 | 
| WebQ      | Best Unsup. | 0.399 | 0.409 | 0.537 | 0.386 | 0.604 |


[1] Semantic Uncertainty: Linguistic Invariances for Uncertainty Estimation in Natural Language Generation https://arxiv.org/abs/2302.09664

**(3) Distribution-shift experiments are too mild to support the deployment claim, and the cost story depends on it. Shifts are within task families; motivating scenarios involve much larger ones. If the predictor doesn't transfer broadly, the offline cost (~100k generations per setup) recurs whenever the deployment shifts, undermining the "lightweight at deployment" framing. (Section 4.2, lines 259–280; Section 4, line 146; Section 5, lines 335–340)
Suggestion: Run at least one cross-task-family transfer experiment (math → code, factoid QA → multi-step reasoning), or analyze what features the calibrator is responding to (representational geometry vs. surface task features) so readers can reason about how often recalibration would be needed in practice.**

Train on SciQ, test on mix of TriviaQA and math (GSM8K or Polymath)

| extra_shift   | Method       |   ECE2 |   Brier |
|:--------------|:-------------|-------:|--------:|
| gsm8k         | Ans. Probs.  |  0.336 |   0.319 |
| gsm8k         | Token Probs. |  0.242 |   0.233 |
| gsm8k         | Verbal Conf. |  0.279 |   0.281 |
| gsm8k         | Ours         |  0.089 |   0.215 |
| polymath      | Ans. Probs.  |  0.336 |   0.320 |
| polymath      | Token Probs. |  0.242 |   0.234 |
| polymath      | Verbal Conf. |  0.279 |   0.281 |
| polymath      | Ours         |  0.121 |   0.226 |



many fewer gens:

|   train_ex |   k_ablate | Method            |   ECE2 |   Brier |
|-----------:|-----------:|:------------------|-------:|--------:|
|        100 |         10 | Ours              | 0.0906 |  0.1642 |
|        100 |         20 | Ours              | 0.0900 |  0.1632 |
|        200 |         10 | Ours              | 0.0863 |  0.1598 |
|        200 |         20 | Ours              | 0.0849 |  0.1583 |
|        - |        - | best unsupervised | 0.2155 |  0.2214 |



**(4) The linguistic-calibration experiment is missing a control that may substantially weaken its headline. The method is compared only against miscalibrated baselines, leaving open whether the win is "this signal is uniquely useful" or just "any well-calibrated signal helps." (Section 4.3, lines 316–333; Table 16)
Suggestion: Add a Test-Time SC condition to the experiment, since Table 1 shows it's similarly calibrated to the distilled method. If downstream performance is comparable, reframe the contribution as "we deliver well-calibrated signals cheaply" rather than "our confidence estimates are uniquely useful."**


| Method       |    Acc |   ECE2 |    MCE |   Brier |
|:-------------|-------:|-------:|-------:|--------:|
| Base Model   | 0.6860 | 0.2749 | 0.3721 |  0.2608 |
| Token Probs. | 0.6561 | 0.2149 | 0.4095 |  0.2483 |
| Ours         | 0.6538 | 0.1279 | 0.2446 |  0.2175 |
| TT-SC        | 0.6548 | 0.1440 | 0.2409 |  0.2168 |
| Verbal Conf. | 0.6467 | 0.3180 | 0.4886 |  0.3097 |



## Reviewer 2


**Limited methodological novelty. The components are familiar: self-consistency as a confidence signal, offline distillation, embedding probes, and isotonic regression. The main contribution is their composition plus a strong empirical study. The paper should avoid overselling the method as algorithmically novel.**


**The supervised comparison is weak. The supervised baseline is Platt scaling on token probabilities. A more informative comparison would train the same embedding-plus-isotonic predictor on true correctness labels. Without this, it is hard to separate the value of self-consistency targets from the value of the predictor architecture. 
Can the authors add a matched supervised baseline using the same embedding-plus-isotonic predictor trained on true correctness labels?**


| Method     |   ECE1 |   ECE2 |    MCE |   Brier |   AUROC |
|:-----------|-------:|-------:|-------:|--------:|--------:|
| Ours       | 0.0696 | 0.0864 | 0.2013 |  0.1550 |  0.7080 |
| Emb. + Iso. Reg.  | 0.0519 | 0.0666 | 0.1755 |  0.1513 |  0.7103 |
| (Current) Supervised | 0.0524 | 0.0649 | 0.1319 |  0.1604 |  0.6524 |


**Self-consistency failures are not diagnosed enough. WebQ appears much weaker than the math datasets, likely because semantically equivalent answers can have different surface forms. The paper notes this issue but does not analyze where or why the self-consistency target breaks down. 
On WebQ, how much of the self-consistency failure comes from correct answers expressed with different surface forms? Did semantic answer clustering improve the target?**

1. webq is least calibrated because it is least accurate for all models; fits well on the accuracy vs. calibration trendlines.
2. webq has the same form as triviaqa, short answers with a set of potential matches.
3. note that, because calibration is generally measured over sets of predictions, diagnosis of individual failures can be difficult; for example, consider a model that outputs 95\% confidence (based on consistency) for 100 task examples, and is correct on 99 of them.  in this case, it is not clear which examples should be analyzed as errors, but it is likely not the case of 95\% consistency with an incorrect answer, which in fact improves calibration.


| Method                      |   ECE1 |   ECE2 |   MCE |   Brier |   AUROC |
|:----------------------------|-------:|-------:|------:|--------:|--------:|
| Ex. Matching |  0.106 |  0.126 | 0.273 |   0.230 |   0.624 |
| Sem. Cluster |  0.121 |  0.141 | 0.285 |   0.228 |   0.657 |
| Best Unsup.  |  0.399 |  0.409 | 0.537 |   0.386 |   0.604 |

**Offline cost is understated. The method requires many offline generations per model and target distribution. This may be reasonable for some local deployments, but in black-box API settings it can be costly and may need to be repeated after domain shifts or model updates. The paper should report token counts or approximate API cost.  
-How does performance scale with the number of unlabeled calibration examples, not only with the number of self-consistency samples per example?
-What is the approximate offline calibration cost in tokens, wall-clock time, or API dollars for a representative black-box model?**


|   train_ex |   k_ablate | Method            |   ECE2 |   Brier |
|-----------:|-----------:|:------------------|-------:|--------:|
|        100 |         10 | Ours              | 0.0906 |  0.1642 |
|        100 |         20 | Ours              | 0.0900 |  0.1632 |
|        200 |         10 | Ours              | 0.0863 |  0.1598 |
|        200 |         20 | Ours              | 0.0849 |  0.1583 |
|        - |        - | best unsupervised | 0.2155 |  0.2214 |

This table estimates the cost of running 1,000 representative math benchmark questions through public model APIs, assuming roughly 250 input tokens and 750 output tokens per question to include both reasoning/explanation and a final answer. Costs are computed from publicly listed per-token API prices, with batch/flex discounts included where available.


| model                              |      cost |
| ---------------------------------- | --------: |
| Gemini 2.5 Flash-Lite  | **$0.16** |
| Gemini 2.5 Flash       | **$0.98** |
| Gemini 3 Flash Preview | **$1.19** |
| GPT-5.4 mini              | **$1.78** |
| Gemini 2.5 Pro         | **$3.91** |
| Claude Haiku 4.5                   | **$4.00** |

To run this with k=10 and n=100 on GSM8K with 1 A100 and vLLM, Qwen3-1.7B takes ~6 minutes, Qwen3-8B takes ~13 minutes.


**Robustness to deployment decoding is incomplete. Training-temperature ablations are useful, but the more practical question is what happens when the deployed model uses a different test-time temperature or greedy decoding. How robust is the predictor when trained at one decoding temperature but deployed with another, especially greedy or low-temperature decoding?**

-All experiments use a different test-time temperature. 
-Qwen3 guidance has a suggested temperature for obtaining correct answers.  It strongly suggests against greedy decoding.


## Reviewer 3


**The main idea feels like a straightforward way to train a cheap model to imitate repeated sampling
My main concern is low novelty. The paper’s core method is to compute self-consistency from repeated offline samples and train a small predictor to approximate that signal at test time. This feels like a direct distillation of test-time self-consistency rather than a new idea. Overall I view the paper as useful but incremental.**



We thank the reviewer, but we want to push back directly on the novelty assessment. The main contribution is not a new estimator, it is a reframing that is absent in prior work: repeated sampling, treated as a test-time procedure in the UQ literature, becomes an offline source of unlabeled supervision, which unlocks an important regime (as recognized by all reviewers) that no existing method serves. Calling this "incremental" because the resulting algorithm is simple inverts how methods should be judged: a simple approach that opens a new deployment regime and works across 9 models, 5 datasets, distribution shift, and black-box access is a stronger result than a complicated one, not a weaker one. We would ask the reviewer to consider whether the same method, dressed up with an unnecessary architecture or other complexities and performing slightly worse, would have read as more novel; because if so, the objection is to the absence of complexity, not the absence of a contribution.


**I am also not fully convinced that the method learns confidence for the specific generated answer, since the question-only ablation is very strong and sometimes close to or better than the full response-based predictor. This suggests that much of the gain may come from learning question difficulty.**

That they are similarly marginally calibrated is unsurprising given that they have the same set of targets.  
What we observe, however, is that the question-only confidence scores tend to bunch more tightly around the average self-consistency rate.
Quantitatively, this can be seen in both the brier score and AUROC.  
In particular AUROC is much worse, and this leads to meaningfully worse selective prediction performance.

Overall, this can be seen in the progression from question-only, to our method with answers, to full test-time SC.  While they all have good marginal calibration, the stronger methods prevail in Brier score and AUROC.

Also, we note that learning model-dependent question difficulty is itself not trivial without access to labels, and is not meaningfully different from the goal of confidence calibration (i.e., it would seem natural for a human to express the difficulty of a problem by giving their estimate of the probability that they complete it successfully).


