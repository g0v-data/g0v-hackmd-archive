Response to Reviewers - AAMAS2027
## Response to Reviewer n9yk

All experimental results reported below are mean ACC_M values over three independent runs. Detailed results will be included in the revised manuscript.

**Experiments that add or remove specialists (Comment 1)**

Without using any accumulated experience, we conduct inference by removing either the specialist with the highest (drop-H) or the lowest (drop-L) Shapley contribution from the specialist team. The results are presented below.

| Dataset | drop-H | drop-L |
|---|---:|---:|
| RareDisease-302 | | |
| RareBench-MME | 2.38 | 8.33 |
| RareBench-HMS | | |

Removing either specialist leads to performance degradation, while removing the highest-contributing specialist results in a greater decrease. These results demonstrate that our contribution estimation captures meaningful differences in specialists' contributions to collaborative diagnosis.

**Experiments on more selection alternatives (Comment 2)**

Using the experience accumulated by our method, we conduct inference with different team selection strategies while keeping the remaining components unchanged.

| Dataset | RareDisease-302 | RareBench-MME | RareBench-HMS |
|---|---:|---:|---:|
| Static global ranking | 45.75 | 30.95 | 34.94 |
| Leave-one-out | 45.35 | 25.00 | 38.71 |
| Random-team | 43.55 | 30.95 | 37.64 |
| Per-specialist-acc | | | |

Our selection strategy still achieves higher ACC_M than these alternative strategies, providing further empirical support for our contribution-based specialist selection.

**Experiments on a single agent with our experience (Comment 3)**

| Dataset | RareDisease-302 | RareBench-MME | RareBench-HMS |
|---|---:|---:|---:|
| Single agent with the same exp. | | | 27.42 |

The specialist-level exp. and our exp. in Table 4 follow identical experimental procedures with comparable inference budgets, differing only in whether feedback from other disciplines is incorporated during experience accumulation. The additional single-agent experiments also yield lower performance than our method. Together, these results support the importance of multidisciplinary interaction during both experience accumulation and utilization.

**The cost of scoring all \(2^I-1\) coalitions per case (Comment 7)**

We further report the token consumption required for Shapley-based contribution estimation.

| Dataset | Avg. input tokens (K) / case | Avg. output tokens (K) / case |
|---|---:|---:|
| RareDisease-302 | 99.54 | 5.30 |
| RareBench-MME | 92.73 | 5.37 |
| RareBench-HMS | 93.85 | 5.21 |

Shapley-based scoring incurs a one-time cost during historical experience accumulation, and the resulting experience can be reused across subsequent cases. Comparisons with alternative team selection strategies further demonstrate that this additional investment in coalition scoring translates into improved diagnostic performance.

**Transfer to RareBench-MME (Comment 5)**

We found that CCMS accounts for 32.1% of MME test cases, most of which are correctly diagnosed using MME-specific experience that provides guidance on distinguishing this disease, whereas none are correctly diagnosed using transferred experience. This largely explains the substantial degradation in ACC_M. However, this does not imply that the accumulated experience is inherently non-reusable. As shown in Fig. 7, transferred experience (including experience from MME) maintains relatively strong performance on RareDisease-302 and HMS, indicating that experience can be reused across datasets when relevant diagnostic knowledge is shared.

**Other concerns (Comments 4, 6, and 8)**

**Train–test overlap.** We adopt case-level random train–test splits, ensuring that each case record is assigned exclusively to either the training or test set.

**ACC_O metric.** The length of the diagnostic candidate list is fixed at 10.

**Overstated claims.** Our conclusion that E²Med “overall achieves competitive or superior performance” is based on a comprehensive consideration of the results across datasets and metrics in Table 1. This statement accounts for variations in performance across experimental settings rather than claiming consistent superiority in every individual setting.

**Team scaling.** Our current experiments primarily investigate system robustness within small-scale multidisciplinary specialist teams, without extending to larger teams. As shown in Fig. 5, we evaluate specialist pools of three and five agents against MDTeamGPT with equally sized specialist pools. The results demonstrate competitive performance and improvements across multiple settings, with more consistent advantages when the specialist pool is expanded to five agents. We agree that extending E²Med to larger teams is an important direction for future research.

**Reproducibility.** Following the conference submission requirements, we have submitted the appendix as a separate ZIP file. It includes the prompts used in our method, hyperparameter configurations, and performance variances across repeated runs to facilitate reproducibility.