# Reviewer CedU, 2（conf3）

Dear Reviewer CedU,

Thank you for your comments and questions.

### Response to Weakness 1 and Question 1

> Weakness 1: Most of the main findings are about rankings that don't agree, and the mean cross-task τ is close to 0. But the authors never rerun the same maintainer on the same artifact, and Reusability and Testability end up comparable only through token counts, so I can't tell whether this disagreement is a real difference or just noise.
>
> Question 1: Are there repeated runs of the same maintainer on the same artifact? What's the test-retest τ or ICC? If there are none, how do you distinguish the disagreement in Findings 1 and 2 from noise?

Our original evaluation prioritized coverage across producers, maintainers, and maintenance demands. To assess stability, we added two independent DeepSeek V4 Flash Stage II runs per evaluation unit, retaining all cases and demands and fixing artifacts, tasks, prompts, tools, and budgets. Including the original, each unit has three measurements.

Three-run producer means ± sample SD are shown below (scores/shares in %, SD in percentage points; tokens in thousands).

| Producer model | Analysability score (%) | Source reuse share (%) | Reusability construction tokens (k) | Testability construction tokens (k) |
| --- | ---: | ---: | ---: | ---: |
| DeepSeek V4 Pro | 86.56 ± 0.79 | 76.56 ± 0.90 | 795.53 ± 12.89 | 268.32 ± 3.46 |
| GLM 5.1 | 86.92 ± 0.46 | 78.88 ± 0.74 | 753.13 ± 5.91 | 314.13 ± 2.15 |
| GLM 5.2 | 89.49 ± 0.44 | 78.57 ± 0.94 | 1279.26 ± 12.29 | 347.34 ± 5.75 |
| HY3 | 91.74 ± 1.08 | 78.28 ± 1.04 | 774.76 ± 8.20 | 326.35 ± 3.21 |
| Kimi K2.7 Code | 89.23 ± 0.55 | 80.10 ± 1.43 | 926.90 ± 9.02 | 358.10 ± 3.47 |
| MiniMax M3 | 89.08 ± 0.86 | 81.91 ± 1.01 | 1036.15 ± 8.56 | 266.32 ± 2.81 |
| GPT-5.6 Sol | 96.10 ± 0.49 | 78.06 ± 0.61 | 584.91 ± 3.98 | 265.41 ± 1.70 |
| Claude Opus 5 | 86.92 ± 1.41 | 80.27 ± 1.19 | 1323.04 ± 3.07 | 224.79 ± 2.28 |

Three-run means remain close to original results (maximum relative SD: 1.78%). Repeatability is assessed using absolute-agreement ICC(A,1) and Kendall’s τ for producer rankings.

| Outcome | ICC(A,1) | Original vs. repeat 1 τ | Original vs. repeat 2 τ | Repeat 1 vs. repeat 2 τ |
| --- | ---: | ---: | ---: | ---: |
| Analysability score | 0.9882 | 0.821 | 0.750 | 0.786 |
| Source reuse share | 0.9799 | 0.857 | 0.786 | 0.929 |
| Reusability construction tokens | 0.9977 | 1.000 | 1.000 | 1.000 |
| Testability construction tokens | 0.9968 | 0.929 | 0.929 | 0.857 |

ICC uses artifact/task-unit measurements (tokens transformed by log(1 + tokens)); τ compares eight-producer rankings. ICC = 0.9799–0.9977 and τ = 0.750–1.000 indicate high repeatability.

### Response to Weakness 2

> Weakness 2: Analysability gives the observer only 5 code inspections for 50 questions. Per Tables A2 and A11, Claude averages 10 source files and scores lowest, while GPT averages only 1.5 and scores highest. I suspect this mostly measures whether the code can be read within 5 calls, not how readable it is.

The five-call budget standardizes inspection effort, and the observer can search multiple files and reuse findings across all 50 questions. Table A11 shows GLM 5.2 achieving higher Analysability than GLM 5.1 despite having more source files. More importantly, across 104 artifacts per maintainer, controlling for case, producer, and language as in Section 4.4, adding log(1 + file count) yields partial R² = 2.56%, 1.41%, and 3.48% for DeepSeek V4 Flash, HY3, and Kimi K2.7 Code. File count thus explains little additional score variation.

File count alone does not capture how code is organized. Our lexical-organization analysis further examines the associations of identifier sharing, cross-file spread, import density, duplication, and local control structure with Analysability.

### Response to Question 3

> Question 3: How was the 5-call inspection limit for Analysability chosen? With a larger budget, do the producer rankings and the Lexical organization association still hold?

An early DeepSeek V4 Flash comparison found producer ordering and lexical-organization associations largely stable as the budget increased. We chose five calls for efficiency and applied that setting to the other maintainers.

DeepSeek V4 Flash scores at 5/10/20 calls (parentheses: change from five calls, percentage points):

| Producer model | 5 calls | 10 calls (change from 5) | 20 calls (change from 5) |
| --- | ---: | ---: | ---: |
| DeepSeek V4 Pro | 86.8% | 86.6% (−0.2) | 87.5% (+0.7) |
| GLM 5.1 | 86.9% | 88.6% (+1.7) | 88.3% (+1.4) |
| GLM 5.2 | 89.2% | 90.9% (+1.7) | 92.2% (+3.0) |
| HY3 | 91.9% | 93.5% (+1.6) | 94.3% (+2.4) |
| Kimi K2.7 Code | 89.7% | 91.7% (+2.0) | 92.8% (+3.1) |
| MiniMax M3 | 89.2% | 90.8% (+1.6) | 92.3% (+3.1) |
| GPT-5.6 Sol | 96.3% | 97.1% (+0.8) | 96.9% (+0.6) |
| Claude Opus 5 | 87.2% | 88.3% (+1.1) | 88.0% (+0.8) |

Scores generally rise with budget; Kendall’s τa is 0.893, 0.893, and 0.929 for 5–10, 5–20, and 10–20 calls.

The lexical organization association under each budget is:

| Inspection budget | Partial R² | Change from 5 calls (percentage points) | q |
| --- | ---: | ---: | ---: |
| 5 | 13.80% | — | 0.0031 |
| 10 | 12.40% | −1.40 | 0.0075 |
| 20 | 10.30% | −3.50 | 0.0180 |

### Response to Question 2 — Permutation test and sample size

> Question 2: In Table A4, blocks with modest partial R² still get very small q values (e.g., the Analysability block has 13.80% with q = 0.0031, despite having 10 components and only 104 samples). Could you describe the permutation test and the effective sample size?

We thank the reviewer for pointing this out. Upon rechecking our analysis, we found an error in the description in Appendix A4.2. The 10 Analysability components were transformed, standardized, and aggregated into a single block score, which was then added to the baseline model as one predictor, consistent with Testability. We apologize for the confusion and will correct the description in the revised manuscript.

Each artifact produces one Analysability score from 50 questions. After excluding self-maintenance, each maintainer panel contains 13 cases × 8 producers = 104 observations. Since producers build independently from empty workspaces, we use case controls and within-case permutations to account for shared task structure.

Specifically, we first fit the baseline model, then shuffle its residuals among the eight artifacts within each case and add them back to the fitted values. We refit both the baseline and full models (including the block score) and recompute partial R², while keeping predictors and case, producer, and language labels fixed. Across 13 cases, the joint permutation space is $(8!)^{13}$.

We repeat this procedure for 20,000 permutations and compute $p=(X+1)/(20{,}001)$, where X counts permutation statistics at least as large as observed. Finally, Benjamini–Hochberg correction across candidate blocks within each outcome–maintainer panel yields q.

# Reviewer vGFm, 3（conf3）

Dear Reviewer vGFm,

Thank you for your helpful suggestions.

### Response to Weakness 1 and Question 2 — Testability protocol

> Weakness 1: Testability covering just seven. Most tasks involve command-line programs, so it is unclear whether the findings generalize to larger, more complex software projects.
>
> Question 2: Could you evaluate Testability using bug detection or mutation testing, rather than only checking whether generated tests reproduce program behavior?

CarryBench evaluates agent-generated code maintainability through downstream tasks beyond functional correctness. For Testability, a fixed tester constructs an executable black-box test suite, with construction tokens measuring the effort required to meet prescribed testing requirements. A key challenge is obtaining reliable ground truth across artifacts that differ in implementation language, internal structure, and functional correctness.

We address this through prescribed behavioral scenarios and observation schemas. For each case, we execute the artifacts through a consistent CLI interface and collect trusted observations of their actual behavior, which serve as artifact-specific ground truth. The tester's submitted tests are then evaluated against these observations, rather than manually specified expected outputs. This allows us to assess whether the tester accurately captures each artifact's behavior, regardless of whether the artifact itself is functionally correct. The same protocol can accommodate new producers without redesigning tasks, while new cases can define their own scenarios and observation schemas to extend coverage.

CLI-based testing also involves substantive testing requirements. For example, Tokei (Appendix A7.3) requires fixture construction, ignore and filtering rules, symbolic-link handling, two output surfaces, and relations between runs. These activities overlap with those involved in bug detection, including constructing inputs, executing programs, and reliably capturing behavioral observations, while our evaluation focuses on the cost of constructing executable tests.
### Response to Weakness 2 — Metric validity

> Weakness 2: Some metrics may not reflect real maintainability. For example, the reuse score counts original code executed through the program interface, which does not necessarily mean the code is easy to reuse or extend. Similarly, Testability focuses on reproducing expected behavior rather than detecting actual bugs.

Section 3.4 separates reuse extent from effort: source reuse share tracks executed task-relevant generated code, including interface invocation, whereas construction tokens count interaction cost through the first accepted submission. High reuse share does not by itself imply easy integration; we will clarify this distinction.

Testability evaluates input construction, execution, and reliable capture of outputs and side effects—skills also needed for bug detection. Its artifact-specific ground truth supports automated comparison, but we do not claim to measure bug-finding effectiveness directly.

### Response to Question 1 — Invocation-based reuse

> Question 1: How much of the reported reuse score comes from simply invoking the original program? Would the conclusions hold if these lines were excluded?

Under Section 3.4 and Appendix A2.2, invocation accounts for 99.90%, 99.90%, and 99.95% of reused-source share for DeepSeek V4 Flash, HY3, and Kimi K2.7 Code (using producer-level artifact means), or 79.03%, 78.33%, and 77.74% of all executed task-relevant code.

Reusing code through program interfaces is legitimate reuse, just as through APIs or library functions. For example, Rhit (Appendix A7.2) invokes existing queries while adding normalization, merging, deduplication, sorting, and policy checks.

Excluding invocation leaves mostly zero scores and insufficient variation for meaningful rankings or cross-maintainer analysis; it would measure only rare copying/adaptation rather than interface-based reuse.

# Reviewer ATVR, 2（conf2）
Dear Reviewer ATVR,

Thank you for your comments and questions.

### Response to Weakness 1 — Central findings and statistical reliability

> Weakness 1: Lack of a clear central finding and low statistical power. While the protocol is sound, the results and figures center around differences and variability rather than a cohesive unifying finding. The finding on tasks and how it affects producer rankings could be strengthened by repeat runs and bootstrap intervals on tau to establish the reliability of these differences. The stability of Reusability rankings is also based upon a partially statistically insignificant p-value (0.068) in the best-case scenario. Figure 3 further shows weak correlations between state cohesion and Analysability and the three other outcomes. It would be helpful for the authors to clarify the substantiality of the findings despite their heterogeneity and limited statistical significance and to provide higher-power analyses if possible.

Our central finding is that maintainability is demand- and maintainer-dependent: producer rankings and associated source characteristics vary with the downstream task and maintainer profile.

Findings 1–2 establish demand-specific rankings and varying cross-maintainer agreement; Finding 4 shows demand- and maintainer-specific source-feature associations. Accordingly, we report separate panels to support producer selection for anticipated downstream work.

To assess reliability, we repeated DeepSeek V4 Flash Stage II evaluations twice, fixing artifacts, tasks, prompts, tools, and budgets, across all cases and demands. Three runs per unit yield ICC(A,1) = 0.9799–0.9977 and between-run producer-ranking τ = 0.750–1.000. Each run covers 104 Analysability evaluations, 104 Reusability evaluations, and 96 Testability task runs across 12 tasks in 7 cases.

These results show high repeatability within outcomes; Question 1 addresses uncertainty in the original cross-demand and cross-maintainer associations.

For Finding 2, all three cross-maintainer source-reuse τ values are positive (two p values: 0.034 and 0.068, the latter not significant at 0.05); Reusability token τ values are also positive (mean 0.49). We claim stronger relative agreement, not significance of every pair.

Figure 3’s weak, mixed-direction cohesion associations further show that this static measure alone cannot substitute for downstream evaluation.

### Response to Question 1 — Bootstrap confidence intervals

> Question 1: Is the disagreement across tasks and maintainers statistically significant, considering the modest differences? It would be helpful to show confidence intervals for tau values (for instance, bootstrapping).

We bootstrapped original cases (2,000 paired resamples), applying common case weights across compared producers and outcomes/maintainers, recomputing producer means and Kendall’s τa (tokens ranked low to high). We report percentile 95% CIs.

For Finding 1, each resample averages the five cross-demand outcome-pair τa values within a maintainer:

| Maintainer profile | Mean τa | 95% confidence interval |
| --- | ---: | --- |
| DeepSeek V4 Flash | +0.04 | [−0.11, +0.23] |
| HY3 | −0.02 | [−0.14, +0.15] |
| Kimi K2.7 Code | −0.07 | [−0.24, +0.04] |

Cross-demand mean τa is near zero, and CI upper bounds remain at most 0.23; together with high repeatability, this supports demand-specific producer selection.

For Finding 2, each resample averages same-outcome τa over three maintainer pairs (Table A3):

| Outcome | Cross-maintainer mean τa | 95% confidence interval |
| --- | ---: | --- |
| Analysability score | +0.16 | [−0.17, +0.41] |
| Source reuse share | +0.46 | [+0.12, +0.71] |
| Reusability construction tokens | +0.49 | [+0.17, +0.71] |
| Testability construction tokens | −0.02 | [−0.21, +0.21] |

Reusability’s mean τa values (0.46, 0.49) have positive 95% CIs.

### Response to Question 4 — Practical producer selection

> Question 4: How should human practitioners use the benchmark or methodology to make critical decisions about which producer to use?

Practitioners can match their downstream maintenance work and maintainer profile to a CarryBench panel; cross-maintainer agreement indicates ranking transferability (Section 5).

For example, MAGIS assigns code localization to a Repository Custodian (Tao et al., 2024), while MetaGPT and AgentCoder assign test construction to specialized agents (Hong et al., 2024; Huang et al., 2024).

Analysability targets source understanding; Reusability share and tokens capture reuse extent and cost; Testability tokens measure test-construction effort. These panels inform role-specific producer choice.

For deployment, practitioners can rerun the protocol with their own maintainer, tasks, and budgets.

### Response to Question 2 — Excluding self-maintenance

> Question 2: Considering the potential risk of biases in either case of including or excluding the same model as a maintainer of itself, why was it chosen to exclude? Could you provide a justification or comparison results if the self model was not excluded?

Self-maintenance may benefit from familiarity with a model’s own naming, organization, or implementation style, confounding comparisons of artifact maintainability.

We therefore exclude producer–maintainer identity pairs; cross-maintainer comparisons use the seven producers common to both profiles.

### Response to Question 3 — AI assistance and human validation

> Question 3: Were the downstream tasks for Reusability, Analysability, and Testability written by humans or AI? Was there any human validation in the process of selecting or validating these tasks?

As disclosed in the AI use statement, AI assisted workflow development and downstream task preparation, with author review.

Analysability questions are derived automatically—not AI-generated—from common-pass generation tests using predefined sampling; the original oracle supplies expected outputs (Section 3.3).

For Reusability and Testability, authors specified objectives, scenarios, and requirements. AI assisted in preparing prompts and supporting task packages, which authors reviewed and corrected before evaluation.

### References

Wei Tao, Yucheng Zhou, Yanlin Wang, Wenqiang Zhang, Hongyu Zhang, and Yu Cheng. [MAGIS: LLM-Based Multi-Agent Framework for GitHub Issue Resolution](https://papers.neurips.cc/paper_files/paper/2024/file/5d1f02132ef51602adf07000ca5b6138-Paper-Conference.pdf). In Advances in Neural Information Processing Systems, 2024.

Sirui Hong, Mingchen Zhuge, Jonathan Chen, Xiawu Zheng, Yuheng Cheng, Ceyao Zhang, Jinlin Wang, Zili Wang, Steven Ka Shing Yau, Zijuan Lin, Liyang Zhou, Chenyu Ran, Lingfeng Xiao, Chenglin Wu, and Jürgen Schmidhuber. [MetaGPT: Meta Programming for a Multi-Agent Collaborative Framework](https://proceedings.iclr.cc/paper_files/paper/2024/file/6507b115562bb0a305f1958ccc87355a-Paper-Conference.pdf). In International Conference on Learning Representations, 2024.

Dong Huang, Jie M. Zhang, Michael Luck, Qingwen Bu, Yuhao Qing, and Heming Cui. [AgentCoder: Multi-Agent-based Code Generation with Iterative Testing and Optimisation](https://arxiv.org/abs/2312.13010). arXiv preprint arXiv:2312.13010, 2024.
