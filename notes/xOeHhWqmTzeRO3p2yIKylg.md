Thank you for your review. New results below are mean ACC_M (%) over three runs. RD302/MME/HMS abbreviate dataset names.

**Validity of Shapley**

We remove either the specialist with the highest (w/o H.) or lowest (w/o L.) Shapley contribution and evaluate the performance (w/o P_int):
||w/o H|w/o L|
|---|---:|---:|
|RD302|41.0|42.4|
|MME|2.4|8.3|
|HMS|27.4|32.2|

The results show that removing either specialist reduces performance, with a greater decrease for w/o H., suggesting that our estimates are informative about specialists' contributions to final diagnosis. 

**Comparison with alternative selection strategies**

We vary only specialist selection, retaining P_int:
||RD302|MME|HMS|
|---|---:|---:|---:|
|Static global ranking|45.7|30.9|34.9|
|Leave-one-out|45.3|25.0|38.7|
|Random-team|43.5|30.9|37.6|
|Ours|48.7|35.7|43.0

Our selection consistently outperforms these alternatives, supporting its effectiveness.

**Value of multi-agent interaction**

In Table 4, specialist-level exp. and our exp. differ only in cross-disciplinary feedback during exp. accumulation with comparable budgets. We further evaluate a single-agent baseline given P_int: 44.0(RD302), 33.3(MME), and 27.4(HMS). Both comparisons favor our method, supporting the value of multi-agent interaction.

**Transfer to MME**

The degradation can be largely explained by the lack of CCMS-related diagnostic guidance in transferred exp., leading to diagnostic failures on CCMS cases, which account for 32.1% of the MME test set. Nevertheless, Fig. 7 shows relatively strong transfer performance on RD302 and HMS, indicating that cross-dataset reuse is feasible.

**Cost of coalition scoring**

The average per-case token cost for coalition scoring (input+output, in K) is 99+5(RD302), 92+5(MME), and 93+5(HMS). This cost is incurred only during exp. accumulation and amortized across subsequent cases.

**Other concerns**

- Metrics and claims: ACC_O fixes the list length at 10. Our claim of overall competitive or superior performance considers all results in Table 1, including the mentioned HMS result.
- Reproducibility and train–test overlap: The separately submitted appendix ZIP contains prompts, hyperparameters, and variances across runs. We will add uncertainty to the main tables. Cases are split into non-overlapping train and test sets.
- Team scaling: Fig. 5 examines robustness across 3- and 5-specialist pools against equally sized MDTeamGPT pools. We leave larger-scale evaluations to future work.