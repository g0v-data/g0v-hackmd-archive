# reviewer3

We thank the reviewer for the positive assessment and suggestions. New results below are mean ACC_M (%) over three runs, and RD302/MME/HMS abbreviate dataset names.

**Q1. Baseline failure analysis**

We further analyzed baseline failures across the three datasets. LLM-based selection omitted the specialist with the highest estimated contribution in 48.7% of test cases. Among the cases that changed from correct to incorrect diagnoses after introducing retrieval in MDTeamGPT, 8.7% showed explicit evidence of diagnostic anchoring. These findings support the two limitations identified in our paper.

**Q2.1. Validity of Shapley**

We estimate Shapley values from static response combinations to reduce computational costs, as full multi-round discussions for all specialist coalitions would require approximately 8× as many LLM calls per case.

Without accumulated cross-disciplinary interaction experience(P_int), we remove either the specialist with the highest (w/o H.) or lowest (w/o L.) Shapley contribution and evaluate the performance:
||w/o H|w/o L|
|---|---:|---:|
|RD302|41.0|42.4|
|MME|2.4|8.3|
|HMS|27.4|32.2|

The results show that removing either specialist reduces performance, with a greater decrease for w/o H., suggesting that our estimates are informative about specialists' contributions to final diagnosis.

**Q2.2. Comparison with alternative selection strategies**

We vary only specialist selection, retaining P_int.

||RD302|MME|HMS|
|---|---:|---:|---:|
|Static global ranking|45.7|30.9|34.9|
|Leave-one-out|45.3|25.0|38.7|
|Random-team|43.5|30.9|37.6|
|Ours|48.7|35.7|43.0

Our strategy outperforms these alternatives, supporting Shapley-based specialist selection.

**Q3. Value of cross-disciplinary interaction Experience**

The comparison between specialist-level exp. and our exp. in Section 4.2.4 (Table 4) was specifically designed to isolate the benefits of cross-disciplinary interaction from general reflection and feedback optimization. Both variants use identical reflection prompts and ground-truth supervision, differing in access to feedback from other disciplines during experience updates. Specialist-level exp. thus corresponds to independent reflection by individual specialists. Both variants use the same team and diagnostic framework during inference, with comparable computational budgets. The gains in Table 4 therefore support the additional value of cross-disciplinary interaction experience.