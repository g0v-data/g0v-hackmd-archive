# Reviewer CedU, 2（conf3）

Dear Reviewer CedU,

Thank you for your comments and questions.

### Response to Weakness 1 and Question 1

> Weakness 1: Most of the main findings are about rankings that don't agree, and the mean cross-task τ is close to 0. But the authors never rerun the same maintainer on the same artifact, and Reusability and Testability end up comparable only through token counts, so I can't tell whether this disagreement is a real difference or just noise.
>
> Question 1: Are there repeated runs of the same maintainer on the same artifact? What's the test-retest τ or ICC? If there are none, how do you distinguish the disagreement in Findings 1 and 2 from noise?

Thank you for your thoughtful comments. Our original evaluation prioritized coverage across producers, maintainers, and maintenance demands. To assess stability, we added two independent Stage II runs using DeepSeek V4 Flash per evaluation unit, retaining all cases and demands and fixing artifacts, tasks, prompts, tools, and budgets. Including the original, each unit has three measurements.

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

Three-run means remain close to the original results, and the maximum relative SD across metrics is 1.78%. Repeatability is assessed using absolute-agreement ICC(A,1) and Kendall’s τ for producer rankings.

| Outcome | ICC(A,1) | Original vs. repeat 1 τ | Original vs. repeat 2 τ | Repeat 1 vs. repeat 2 τ |
| --- | ---: | ---: | ---: | ---: |
| Analysability score | 0.9882 | 0.821 | 0.750 | 0.786 |
| Source reuse share | 0.9799 | 0.857 | 0.786 | 0.929 |
| Reusability construction tokens | 0.9977 | 1.000 | 1.000 | 1.000 |
| Testability construction tokens | 0.9968 | 0.929 | 0.929 | 0.857 |

ICC is computed at the artifact or task-unit level (tokens transformed by log(1 + tokens)); τ compares rankings based on the eight producers’ mean outcomes. ICC = 0.9799–0.9977 and τ = 0.750–1.000 indicate high repeatability.

### Response to Weakness 2

> Weakness 2: Analysability gives the observer only 5 code inspections for 50 questions. Per Tables A2 and A11, Claude averages 10 source files and scores lowest, while GPT averages only 1.5 and scores highest. I suspect this mostly measures whether the code can be read within 5 calls, not how readable it is.

Thank you for your sincere comments. The five-call budget provides a common inspection limit, and the observer can search multiple files by one call and reuse findings across all 50 questions. Table A11 shows GLM 5.2 achieving higher Analysability than GLM 5.1 despite having more source files. More importantly, across 104 artifacts per maintainer, controlling for case, producer, and language as in Section 4.4, adding log(1 + source file count) yields partial R² = 2.56%, 1.41%, and 3.48% for DeepSeek V4 Flash, HY3, and Kimi K2.7 Code. Source file count is one factor associated with Analysability, but its additional explanatory contribution is relatively small. Our lexical organization analysis further examines the associations of identifier sharing, cross-file spread, import density, duplication, and local control structure with Analysability.

### Response to Question 3

> Question 3: How was the 5-call inspection limit for Analysability chosen? With a larger budget, do the producer rankings and the Lexical organization association still hold?

Thank you for your question. An early DeepSeek V4 Flash comparison found producer ordering and lexical organization associations largely stable as the budget increased. We chose five calls for efficiency and applied that setting to the other maintainers.

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

### Response to Question 2 

> Question 2: In Table A4, blocks with modest partial R² still get very small q values (e.g., the Analysability block has 13.80% with q = 0.0031, despite having 10 components and only 104 samples). Could you describe the permutation test and the effective sample size?

Thank you for pointing out this issue. Upon rechecking our analysis, we found an error in the description in Appendix A4.2. The 10 components of the lexical organization block were transformed, standardized, and aggregated into a single block score, which was then added to the baseline model as one predictor, consistent with Testability. We apologize for the confusion and will correct the description in the revised manuscript.

Each artifact produces one Analysability score from 50 questions. After excluding self-maintenance, each maintainer panel contains 13 cases × 8 producers = 104 observations. Producers build independently from empty workspaces, and we use case controls and within-case permutations to account for shared task structure.

Specifically, we first fit the baseline model, then shuffle its residuals among the eight artifacts within each case and add them back to the fitted values. We refit both the baseline and full models (including the block score) and recompute partial R², while keeping predictors and case, producer, and language labels fixed. Across 13 cases, the joint permutation space is $(8!)^{13}$.

We repeat this procedure for 20,000 permutations and compute $p=(X+1)/(20{,}001)$, where X counts permutation statistics at least as large as observed. Finally, Benjamini–Hochberg correction across candidate blocks within each outcome–maintainer panel yields q.

# Reviewer vGFm, 3（conf3）

Dear Reviewer vGFm,

Thank you for your comments and questions.

### Response to Weakness 1 and Question 2

> Weakness 1: Testability covering just seven. Most tasks involve command-line programs, so it is unclear whether the findings generalize to larger, more complex software projects.
>
> Question 2: Could you evaluate Testability using bug detection or mutation testing, rather than only checking whether generated tests reproduce program behavior?

Thank you for your thoughtful questions. CarryBench evaluates agent-generated code maintainability through downstream tasks beyond functional correctness. For Testability, a fixed tester constructs an executable black-box test suite, with construction tokens measuring the effort required to meet prescribed testing requirements. A key challenge is obtaining reliable ground truth across artifacts that differ in implementation language, internal structure, and functional correctness.

We define behavioral scenarios and observation schemas per case, then obtain trusted execution observations through a consistent CLI interface as artifact-specific ground truth. Mutation testing would additionally require valid mutation operators and comparable detection criteria across heterogeneous implementations. Observations produced by the submitted test suite are compared against these trusted observations, without requiring manually specified expected outputs for each implementation. This allows us to assess whether the tester accurately captures each artifact's behavior, regardless of its functional correctness. The same protocol supports new producers without redesigning tasks, while new cases can define their own scenarios and observation schemas to extend coverage.

Tokei (Appendix A7.3) illustrates substantive CLI-based testing: fixture construction, ignore and filtering rules, symbolic-link handling, two output surfaces, and relations between runs. Bug detection likewise requires constructing inputs, executing programs, and reliably observing their behavior before deviations from expected behavior can be identified. Our evaluation measures the cost of these test-construction activities.

### Response to Weakness 2

> Weakness 2: Some metrics may not reflect real maintainability. For example, the reuse score counts original code executed through the program interface, which does not necessarily mean the code is easy to reuse or extend. Similarly, Testability focuses on reproducing expected behavior rather than detecting actual bugs.

Thank you for your comments. In Section 3.4, source reuse share tracks executed task-relevant code provenance, including interface-based invocation, while construction tokens measure the interaction cost through the first accepted submission. Together, these metrics distinguish reuse extent from integration effort, as a high source reuse share does not necessarily imply easier reuse. We will clarify their complementary roles in the revision.

For Testability, constructing inputs, executing programs, and reliably capturing outputs and execution effects are common activities in software testing. These activities also support bug detection, where observed behavior is compared against expected behavior to identify potential faults. Our Testability task evaluates the effort required to construct executable black-box tests that accurately capture an artifact's behavior under prescribed scenarios.

### Response to Question 1

> Question 1: How much of the reported reuse score comes from simply invoking the original program? Would the conclusions hold if these lines were excluded?

Thank you for your question. Our analysis shows that artifact invocation accounts for 99.90%, 99.90%, and 99.95% of source reuse share under DeepSeek V4 Flash, HY3, and Kimi K2.7 Code, respectively. When measured against all executed task-relevant code, the corresponding percentages are 79.03%, 78.33%, and 77.74%. These results are based on artifact-level averages for each producer.

As explained under Weakness 1 and Question 2, the CLI provides a consistent interaction contract. Reusing functionality through library functions, APIs, or program interfaces is common software-engineering practice: consumers invoke existing implementations and add integration logic rather than copying or reimplementing functionality. Our CLI-based Reusability task therefore predominantly uses artifact invocation. For example, the Rhit consumer (Appendix A7.2) invokes existing queries while adding normalization, merging, deduplication, sorting, and policy checks to construct a new case-specific workflow.

Excluding invocation lines would leave only source copying or adaptation, which is uncommon in our tasks. Most scores would become zero, leaving insufficient variation for meaningful producer rankings or cross-maintainer agreement analysis. We therefore retain invocation lines because using existing functionality through program interfaces is itself a form of reuse.

# Reviewer ATVR, 2（conf2）
Dear Reviewer ATVR,

Thank you for your comments and questions.

### Response to Weakness 1

> Weakness 1: Lack of a clear central finding and low statistical power. While the protocol is sound, the results and figures center around differences and variability rather than a cohesive unifying finding. The finding on tasks and how it affects producer rankings could be strengthened by repeat runs and bootstrap intervals on tau to establish the reliability of these differences. The stability of Reusability rankings is also based upon a partially statistically insignificant p-value (0.068) in the best-case scenario. Figure 3 further shows weak correlations between state cohesion and Analysability and the three other outcomes. It would be helpful for the authors to clarify the substantiality of the findings despite their heterogeneity and limited statistical significance and to provide higher-power analyses if possible.

Thank you for your sincere comments. Our central finding is that maintainability should be evaluated separately for each maintenance demand under a specified maintainer profile. Finding 1 supports separating demands because producers rank differently for understanding, reusing, and testing code. Finding 2 supports accounting for the maintainer because these rankings do not transfer equally well across maintainers. Finding 4 further motivates demand-specific optimization research, as the source characteristics associated with performance vary across demands and maintainers. We discuss the practical implications under Question 4 and will clarify this central finding in the revision.

To assess the reliability of our results, we conducted additional repeated evaluations using DeepSeek V4 Flash across all cases and three maintenance demands. We fixed the Stage I artifacts, questions or tasks, prompts, tools, and budgets, and performed two additional independent Stage II runs, yielding three measurements per evaluation unit, including the original run. Each run includes 104 Analysability evaluations, 104 Reusability evaluations, and 96 Testability task runs covering 12 task instances across 7 independent cases.

We report single-measurement absolute-agreement ICC and between-run Kendall's τ for producer rankings:

| Outcome | ICC(A,1) | Original vs. repeat 1 τ | Original vs. repeat 2 τ | Repeat 1 vs. repeat 2 τ |
| --- | ---: | ---: | ---: | ---: |
| Analysability score | 0.9882 | 0.821 | 0.750 | 0.786 |
| Source reuse share | 0.9799 | 0.857 | 0.786 | 0.929 |
| Reusability construction tokens | 0.9977 | 1.000 | 1.000 | 1.000 |
| Testability construction tokens | 0.9968 | 0.929 | 0.929 | 0.857 |

The high ICC values (0.9799–0.9977) and between-run ranking τ values (0.750–1.000) indicate that producer rankings are relatively stable within each outcome, despite the low cross-demand agreement reported in Finding 1. We further examine uncertainty in the original cross-demand and cross-maintainer comparisons through paired case bootstrap under Question 1.

Regarding Finding 2, all three cross-maintainer τ values for source reuse share are positive, although one comparison has p = 0.068. Our paired case bootstrap further yields positive confidence intervals for the mean cross-maintainer agreement in both source reuse share (0.46, 95% CI [0.12, 0.71]) and Reusability construction tokens (0.49, 95% CI [0.17, 0.71]). These results support relatively stronger cross-maintainer agreement for Reusability without implying statistical significance for every maintainer pair.

Figure 3 further reinforces the importance of downstream evaluation. Its weak, mixed-direction associations between static cohesion and maintenance outcomes suggest that this measure alone is insufficient to characterize maintainability across different demands.
### Response to Question 1

> Question 1: Is the disagreement across tasks and maintainers statistically significant, considering the modest differences? It would be helpful to show confidence intervals for tau values (for instance, bootstrapping).

Thank you for your question. We bootstrapped original cases (2,000 paired resamples), applying common case weights across producers and the outcomes or maintainer profiles being compared, recomputing producer means and Kendall’s τa (tokens ranked low to high). We report percentile 95% CIs.

For Finding 1, each resample averages the five cross-demand outcome-pair τa values within a maintainer:

| Maintainer profile | Mean τa | 95% confidence interval |
| --- | ---: | --- |
| DeepSeek V4 Flash | +0.04 | [−0.11, +0.23] |
| HY3 | −0.02 | [−0.14, +0.15] |
| Kimi K2.7 Code | −0.07 | [−0.24, +0.04] |

Cross-demand mean τa is near zero, and CI upper bounds remain at most 0.23; together with high repeatability, this supports demand-specific producer selection.

For Finding 2, each resample averages τa for the same outcome across the three maintainer pairs (Table A3):

| Outcome | Cross-maintainer mean τa | 95% confidence interval |
| --- | ---: | --- |
| Analysability score | +0.16 | [−0.17, +0.41] |
| Source reuse share | +0.46 | [+0.12, +0.71] |
| Reusability construction tokens | +0.49 | [+0.17, +0.71] |
| Testability construction tokens | −0.02 | [−0.21, +0.21] |

Both Reusability outcomes have 95% CIs entirely above zero.

### Response to Question 4 

> Question 4: How should human practitioners use the benchmark or methodology to make critical decisions about which producer to use?

Thank you for your thoughtful question. Section 5 explains how to select producers for the intended maintenance demand and maintainer profile.

For source understanding and behavioral analysis, practitioners can prioritize Analysability score. For building new consumers, source reuse share and construction tokens capture reuse extent and cost; for test construction, practitioners can compare Testability construction tokens. Multi-agent software engineering illustrates these demands: MAGIS assigns code localization to a Repository Custodian (Tao et al., 2024), while MetaGPT and AgentCoder assign test construction to specialized agents (Hong et al., 2024; Huang et al., 2024).

Practitioners should use the panel matching their downstream maintainer and examine cross-maintainer agreement to assess whether producer rankings transfer. Lower agreement motivates reevaluating producer choices when the maintainer changes, particularly for Analysability and Testability.

Practitioners can also apply the same protocol in their deployment environments, using their actual maintainer profiles, tasks, and budgets to inform producer selection.

### Response to Question 2

> Question 2: Considering the potential risk of biases in either case of including or excluding the same model as a maintainer of itself, why was it chosen to exclude? Could you provide a justification or comparison results if the self model was not excluded?

Thank you for your comments. CarryBench evaluates maintainability through the downstream performance of fixed maintainer models. Different producers may generate code with distinct naming conventions, source organization, and implementation patterns. A model’s own outputs may align more closely with these patterns, introducing an additional distributional alignment factor. We therefore exclude producer–maintainer identity pairs to reduce its influence on maintainability comparisons. Cross-maintainer comparisons retain the seven producers evaluated by both profiles, ensuring a consistent candidate set.

As requested, we also report the excluded self-maintenance results:

| Producer–maintainer pair | Analysability score (%) ↑ | Source reuse share (%) ↑ | Reusability construction tokens (× profile median) ↓ | Testability construction tokens (× profile median) ↓ |
| --- | ---: | ---: | ---: | ---: |
| DeepSeek V4 Flash | 92.15 (2/9) | 75.04 (9/9) | 0.92 (4/9) | 0.83 (2/9) |
| HY3 | 88.62 (5/9) | 77.82 (6/9) | 1.47 (8/9) | 0.84 (3/9) |
| Kimi K2.7 Code | 94.46 (1/9) | 82.77 (2/9) | 1.72 (9/9) | 1.01 (5/9) |

Parentheses indicate ranks among all nine producers under the corresponding maintainer, with 1 being best. Construction tokens use the same normalization denominators as Figure 2: the median producer-level cost among the eight non-self producers in each maintainer profile. 
### Response to Question 3 

> Question 3: Were the downstream tasks for Reusability, Analysability, and Testability written by humans or AI? Was there any human validation in the process of selecting or validating these tasks?

Thank you for your questions. As disclosed in our AI use statement, AI assisted with benchmark workflow development and downstream task preparation, and all AI-assisted work was reviewed by the authors.

For Analysability, questions were automatically derived from common-pass generation tests using predefined sampling rules, rather than generated by AI. As described in Section 3.3, the original behavioral oracle provides the expected outputs and grading criteria.

For Reusability and Testability, the authors defined the task objectives, behavioral scenarios, and evaluation requirements. AI assisted in preparing the task prompts and supporting materials, which were subsequently reviewed and corrected by the authors before evaluation.

### References

Wei Tao, Yucheng Zhou, Yanlin Wang, Wenqiang Zhang, Hongyu Zhang, and Yu Cheng. [MAGIS: LLM-Based Multi-Agent Framework for GitHub Issue Resolution](https://papers.neurips.cc/paper_files/paper/2024/file/5d1f02132ef51602adf07000ca5b6138-Paper-Conference.pdf). In Advances in Neural Information Processing Systems, 2024.

Sirui Hong, Mingchen Zhuge, Jonathan Chen, Xiawu Zheng, Yuheng Cheng, Ceyao Zhang, Jinlin Wang, Zili Wang, Steven Ka Shing Yau, Zijuan Lin, Liyang Zhou, Chenyu Ran, Lingfeng Xiao, Chenglin Wu, and Jürgen Schmidhuber. [MetaGPT: Meta Programming for a Multi-Agent Collaborative Framework](https://proceedings.iclr.cc/paper_files/paper/2024/file/6507b115562bb0a305f1958ccc87355a-Paper-Conference.pdf). In International Conference on Learning Representations, 2024.

Dong Huang, Jie M. Zhang, Michael Luck, Qingwen Bu, Yuhao Qing, and Heming Cui. [AgentCoder: Multi-Agent-based Code Generation with Iterative Testing and Optimisation](https://arxiv.org/abs/2312.13010). arXiv preprint arXiv:2312.13010, 2024.

