Thank you for your review. New results below are mean ACC_M(%) over three runs. RD302/MME/HMS abbreviate dataset names.

**Statistical reliability**

Train/test sizes (30/70 split) are 90/212(RD302), 12/28(MME) and 26/62(HMS).
We computed 95% CIs and paired permutation tests against MDTeamGPT(MDT), the overall strongest baseline. \* denotes p < 0.05.
|||ACC_M|ACC_O|
|---|---|---|---|
|RD302|our|[42.4,55.0]|**[70.6,81.4]**\*|
||MDT|[38.3,50.7]|[56.6,68.7]|
|MME|our|[19.0,53.5]|[46.4,76.1]|
||MDT|[16.6,51.1]|[36.9,72.6]|
|HMS|our|[31.1,55.3]|**[68.8,88.1]**\*|
||MDT|[26.8,49.4]|[45.7,69.3]|

E2Med achieves higher accuracy in all 6 comparisons, with significant ACC_O improvements on RD302 and HMS, supporting its effectiveness in differential diagnosis and competitive performance in the remaining settings.

**Stability of exp. accumulation**

We further shuffled cases in accumulation and evaluate: 48.9±0.4(RD302), 35.7±0.0(MME), and 44.0±0.7(HMS). Comparable means and limited variance suggest robustness.

**Alternative selection strategies**

We vary only specialist selection, retaining P_int:
||RD302|MME|HMS|
|---|---:|---:|---:|
|Static global ranking|45.7|30.9|34.9|
|Leave-one-out|45.3|25.0|38.7|
|Random-team|43.5|30.9|37.6|
|Ours|48.7|35.7|43.0

Our strategy outperforms these alternatives.

**Train–test overlap and exp. transfer**

Cases with seen labels (a test case is considered seen if any disease label appears in training): 1/212(RD302), 9/28(MME), and 38/62(HMS). P_int contains both general collaboration strategies and disease diagnostic knowledge. The degradation mentioned may reflect both a lack of relevant diagnostic guidance and differences in team composition: transferred exp. lacks CCMS-specific guidance, leading to failures on CCMS cases (32.1% of the MME test set), while the no-exp. baseline in Table 2 uses the full team rather than dynamic selection.

**Other concerns**
- Test-set sizes: We acknowledge the limited test-set sizes due to the scarcity of publicly accessible cases. Nevertheless, three datasets and two LLMs enable evaluation across diverse settings.
- Configurations: DeepSeek-R1 serves as the accuracy judge. The loss critic, gradient critic, optimizer, and summarizer are same as the reasoning backbone. Agreement with clinicians remains to be evaluated.
- More analysis of Fig. 8: Without P_int, the team ranked another disease first in Fig. 8's case. In other runs with P_int, the team also shifted toward SAPHO during discussion.