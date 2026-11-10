# Reviewer CedU, 2（conf3）

Dear Reviewer CedU,

Thank you for your comments and questions.

### Response to Weakness 1 and Question 1

> Weakness 1: Most of the main findings are about rankings that don't agree, and the mean cross-task τ is close to 0. But the authors never rerun the same maintainer on the same artifact, and Reusability and Testability end up comparable only through token counts, so I can't tell whether this disagreement is a real difference or just noise.
>
> Question 1: Are there repeated runs of the same maintainer on the same artifact? What's the test-retest τ or ICC? If there are none, how do you distinguish the disagreement in Findings 1 and 2 from noise?

Given repository-level evaluation costs, we prioritized coverage across producer models, maintainer profiles, and maintenance demands. To assess stability, we added two independent Stage II runs using DeepSeek V4 Flash, balancing capability and cost while retaining all cases and demands. Stage I artifacts, questions or tasks, prompts, tools, and budgets were fixed, yielding three measurements per evaluation unit including the original run.

The table reports mean ± sample standard deviation of each producer's average performance across three runs. Analysability score and source reuse share are percentages (standard deviations in percentage points); construction tokens are in thousands.

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

Three-run means remain close to the original results, with a maximum relative standard deviation of 1.78%. We also report single-measurement absolute-agreement ICC and between-run Kendall's τ for producer rankings.

| Outcome | ICC(A,1) | Original vs. repeat 1 τ | Original vs. repeat 2 τ | Repeat 1 vs. repeat 2 τ |
| --- | ---: | ---: | ---: | ---: |
| Analysability score | 0.9882 | 0.821 | 0.750 | 0.786 |
| Source reuse share | 0.9799 | 0.857 | 0.786 | 0.929 |
| Reusability construction tokens | 0.9977 | 1.000 | 1.000 | 1.000 |
| Testability construction tokens | 0.9968 | 0.929 | 0.929 | 0.857 |

ICC uses artifact or downstream task-unit measurements, with construction tokens transformed by log(1 + tokens). Kendall's τ compares the eight producers' average-performance rankings. ICC values of 0.9799–0.9977 and τ values of 0.750–1.000 indicate high measurement and ranking consistency across runs.

### Response to Weakness 2

> Weakness 2: Analysability gives the observer only 5 code inspections for 50 questions. Per Tables A2 and A11, Claude averages 10 source files and scores lowest, while GPT averages only 1.5 and scores highest. I suspect this mostly measures whether the code can be read within 5 calls, not how readable it is.

A fixed source inspection budget compares Analysability under matched effort to locate logic, trace cross-file dependencies, and understand behavior. The observer can search multiple files and reuse information across all 50 questions.

Table A11 suggests that file count alone does not explain Analysability differences: GLM 5.2 averages 8.308 source files and scores 89.2% and 86.9% under DeepSeek V4 Flash and HY3, versus 2.231 files and scores of 86.9% and 86.3% for GLM 5.1. On statix, HY3 inspected three relevant files within five calls and scored 94% on GLM 5.2's eight-file implementation, versus 90% on GLM 5.1's single-file implementation. Thus, relevant behavior can be located and understood within the budget even across multiple files; effort also depends on source organization.

We also examined the association between source file count and Analysability across all 104 artifacts under each maintainer profile. Following the regression setup in Section 4.4, we controlled for case, producer model, and implementation language. Adding log(1 + source file count) yielded partial R² values of 2.56%, 1.41%, and 3.48% for DeepSeek V4 Flash, HY3, and Kimi K2.7 Code, respectively. Thus, source file count explains only a small proportion of the variation remaining after these controls.

File count affects the search space and may covary with naming and logic distribution. Our lexical organization finding examines the conditional association of identifier sharing and cross-file spread, import density, duplication, and local control structure with Analysability.

### Response to Question 3

> Question 3: How was the 5-call inspection limit for Analysability chosen? With a larger budget, do the producer rankings and the Lexical organization association still hold?

Our early DeepSeek V4 Flash comparison showed that increasing the budget largely preserved producer ordering and the lexical organization association. We therefore chose five calls for cost and efficiency, then extended this setting to HY3 and Kimi K2.7 Code.

The table compares DeepSeek V4 Flash at 5, 10, and 20 calls; parentheses give percentage-point changes from five calls.

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

Scores generally increase with budget, with ranking changes concentrated among similarly scoring producers. From the displayed scores, Kendall's τa for 5 vs. 10, 5 vs. 20, and 10 vs. 20 calls is 0.893, 0.893, and 0.929, respectively.

The lexical organization association under each budget is:

| Inspection budget | Partial R² | Change from 5 calls (percentage points) | q |
| --- | ---: | ---: | ---: |
| 5 | 13.80% | — | 0.0031 |
| 10 | 12.40% | −1.40 | 0.0075 |
| 20 | 10.30% | −3.50 | 0.0180 |

Partial R² decreases with budget, while q remains < 0.05 throughout.

### Response to Question 2

> Question 2: In Table A4, blocks with modest partial R² still get very small q values (e.g., the Analysability block has 13.80% with q = 0.0031, despite having 10 components and only 104 samples). Could you describe the permutation test and the effective sample size?

A careful check of our analysis and its description identified an inconsistency in Appendix A4.2. The actual analysis applies the specified transformations and standardization to the 10 components, aggregates them into one block score, and adds it to the baseline model: one additional predictor, consistent with Testability's composite scores. Appendix A4.2 incorrectly describes separate component columns. We apologize and will correct this description in the revision.

The analysis unit is the artifact: its 50 behavioral questions yield one Analysability score, with maintainer profiles analyzed separately. Excluding producer–maintainer identity pairs leaves 13 cases × 8 producers = 104 observations per panel. Within each case, producers independently build from empty workspaces, yielding different internal structures and potentially different implementation languages. This provides artifact-level variation, while case controls and within-case residual permutations account for shared task structure.

We fit the baseline model, permute its residuals among the eight artifacts within each case, and add them to the original fitted values. We then refit the baseline and full models, the latter containing the block score, and calculate Partial R². The block score and case, producer, and language labels remain fixed, so each permutation tests the gain from the same score. Across 13 cases, the joint permutation space is $(8!)^{13}$; each draw yields a statistic for the complete 104-artifact panel.

For 20,000 random permutations, $p=(X+1)/(B+1)$, where $B=20{,}000$ and $X$ counts permutation statistics at least as large as observed. Benjamini–Hochberg (BH) correction across all candidate blocks for the same outcome and maintainer profile gives q.

# Reviewer vGFm, 3（conf3）

Dear Reviewer vGFm,

Thank you for your helpful suggestions.

### Response to Weakness 1 and Question 2

> Weakness 1: Testability covering just seven. Most tasks involve command-line programs, so it is unclear whether the findings generalize to larger, more complex software projects.
>
> Question 2: Could you evaluate Testability using bug detection or mutation testing, rather than only checking whether generated tests reproduce program behavior?

CarryBench evaluates agent-generated code maintainability through downstream tasks beyond functional correctness. For Testability, a fixed tester constructs an executable black-box test suite; construction tokens measure the cost of meeting prescribed test-construction requirements.

The design requires consistent test requirements and automatically obtainable ground truth across artifacts differing in internal structure, implementation language, and functional correctness. Manually designing tests and expected results for each implementation would limit scalability to new producers and cross-producer comparability. Mutation testing likewise requires applicable operators, valid mutations, and comparable detection requirements across heterogeneous implementations. We therefore use prescribed behavioral scenarios and execution observations.

The CLI provides a consistent interface across implementation languages. We define behavioral scenarios and an observation schema per case, then automatically obtain trusted execution observations as artifact-specific ground truth. The tester must capture the current artifact's behavior accurately, regardless of its functional correctness. New producers can thus use the same task protocol without redesigned tasks or manually specified outputs, which is a key reason for prioritizing CLI programs.

The same design also supports expanding case coverage. New cases can define their behavioral scenarios and observation schemas while reusing the controlled execution interface and acceptance mechanism based on trusted observations. Together, these capabilities provide a path toward evaluating a broader range of cases, including larger and more complex software projects.

CLI tasks also support diverse testing requirements: Tokei (Appendix A7.3) involves fixture construction, ignore and filtering rules, symbolic-link handling, two output surfaces, and relations between runs. These activities are closely related to bug detection and mutation testing: detecting behavioral faults involves constructing inputs, executing programs, and reliably extracting observations to identify deviations from test criteria. Our task evaluates these activities against artifact-specific ground truth, enabling consistent, automated comparison of downstream test-construction costs.

### Response to Weakness 2

> Weakness 2: Some metrics may not reflect real maintainability. For example, the reuse score counts original code executed through the program interface, which does not necessarily mean the code is easy to reuse or extend. Similarly, Testability focuses on reproducing expected behavior rather than detecting actual bugs.

Section 3.4 reports source reuse share and construction tokens separately to characterize the extent and cost of using an existing implementation in a new consumer. Source reuse share tracks executed task-relevant code provenance, counting interface-based invocation as direct reuse. Construction tokens measure cumulative interaction cost through the first accepted submission, capturing reuse or extension effort. Together, they distinguish extensive reuse accompanied by substantial integration cost: higher source reuse share alone does not imply easier reuse. We will clarify these complementary roles in the revision.

Constructing inputs, executing programs, and capturing outputs and execution effects are common testing activities also used in bug detection. Bug detection typically compares actual observations against test criteria, making reliable behavior capture important. Our Testability task operationalizes this through executable black-box test suite construction: accurately representing observations and relations between runs under prescribed scenarios, with construction tokens measuring the cost. As explained under Weakness 1 and Question 2, trusted artifact-specific observations provide automatic ground truth for consistent evaluation across implementations.

### Response to Question 1

> Question 1: How much of the reported reuse score comes from simply invoking the original program? Would the conclusions hold if these lines were excluded?

Following Section 3.4 and Appendix A2.2, we separated generated-source lines reached through artifact invocation from reused source incorporated into the consumer. Using artifact means per producer, invocation contributes 99.90%, 99.90%, and 99.95% of source reuse share under DeepSeek V4 Flash, HY3, and Kimi K2.7 Code, respectively. These percentages concern reused source; invocation accounts for 79.03%, 78.33%, and 77.74% of all executed task-relevant code.

As explained under Weakness 1 and Question 2, the CLI provides a consistent interaction contract. Reusing functionality through library functions, APIs, or program interfaces is common software-engineering practice: consumers invoke existing implementations and add integration logic rather than copying or reimplementing functionality. Our CLI-based Reusability task therefore predominantly uses artifact invocation. For example, the Rhit consumer (Appendix A7.2) invokes existing queries and adds normalization, merging, deduplication, sorting, and policy checks. This contribution to a new case-specific workflow motivates counting invocation as direct reuse in Section 3.4.

Excluding invocation lines would leave only source copying or adaptation, which is uncommon in our current task. Most scores would become zero, leaving insufficient variation for meaningful producer-ranking or cross-maintainer agreement analyses. More importantly, invoking existing functionality through program interfaces is itself a form of reuse, which is why we retain these lines in the metric.

# Reviewer ATVR, 2（conf2）
Dear Reviewer ATVR,

Thank you for your comments and questions.

### Response to Weakness 1

> Weakness 1: Lack of a clear central finding and low statistical power. While the protocol is sound, the results and figures center around differences and variability rather than a cohesive unifying finding. The finding on tasks and how it affects producer rankings could be strengthened by repeat runs and bootstrap intervals on tau to establish the reliability of these differences. The stability of Reusability rankings is also based upon a partially statistically insignificant p-value (0.068) in the best-case scenario. Figure 3 further shows weak correlations between state cohesion and Analysability and the three other outcomes. It would be helpful for the authors to clarify the substantiality of the findings despite their heterogeneity and limited statistical significance and to provide higher-power analyses if possible.

CarryBench operationalizes the maintainability of agent-generated code through downstream evaluations that distinguish maintenance demands and maintainer profiles. Our findings show that different maintenance demands yield different producer rankings and are associated with different source characteristics, with these patterns also varying across maintainer profiles.

Specifically, Findings 1 and 2 show that producer rankings differ across maintenance demands, while cross-maintainer agreement also varies by demand. Finding 4 further identifies different source-feature associations across maintenance demands and maintainer profiles. Together, these findings motivate evaluating maintainability in the context of specific downstream work. We therefore report outcomes separately, allowing practitioners to select the panel corresponding to their anticipated maintenance tasks.

We assess run-to-run reliability with fixed-artifact, fixed-protocol repeated evaluations, and report bootstrap uncertainty for the original ranking associations under Question 1.

Repeated evaluation uses DeepSeek V4 Flash across all cases and three maintenance demands. Excluding producer–maintainer identity pairs leaves eight producers per panel. Two additional independent Stage II runs, with Stage I artifacts, questions or tasks, prompts, tools, and budgets fixed, yield three measurements including the original. Each run includes 104 Analysability evaluations, 104 Reusability evaluations, and 96 Testability task runs over 12 task instances and 7 independent cases. Below are single-measurement absolute-agreement ICC and between-run Kendall's τ for producer rankings.

| Outcome | ICC(A,1) | Original vs. repeat 1 τ | Original vs. repeat 2 τ | Repeat 1 vs. repeat 2 τ |
| --- | ---: | ---: | ---: | ---: |
| Analysability score | 0.9882 | 0.821 | 0.750 | 0.786 |
| Source reuse share | 0.9799 | 0.857 | 0.786 | 0.929 |
| Reusability construction tokens | 0.9977 | 1.000 | 1.000 | 1.000 |
| Testability construction tokens | 0.9968 | 0.929 | 0.929 | 0.857 |

ICC values of 0.9799–0.9977 and τ values of 0.750–1.000 show high measurement and producer-ranking repeatability within outcomes. Question 1 separately addresses uncertainty in the original cross-demand and cross-maintainer comparisons.

Finding 2 distinguishes relative agreement from statistical significance. All three cross-maintainer τ values for source reuse share are positive; two have p = 0.034 and 0.068, the latter above 0.05. All three Reusability construction-token coefficients are also positive, averaging 0.49. Finding 2 describes stronger cross-maintainer agreement for Reusability than other demands.

Figure 3 examines whether state cohesion can substitute for downstream evaluation. Weak associations with mixed directions do not support this static measure alone as a proxy for maintenance outcomes. Together, the findings support distinguishing demands and maintainer profiles when selecting producers for a target workflow.

### Response to Question 1

> Question 1: Is the disagreement across tasks and maintainers statistically significant, considering the modest differences? It would be helpful to show confidence intervals for tau values (for instance, bootstrapping).

We applied paired case bootstrap to the original data: 2,000 resamples with percentile 95% confidence intervals. Each resample uses common case weights across producers and compared outcomes or maintainer profiles, recomputes producer-level outcomes, and calculates Kendall's τa. Construction tokens rank from low to high.

For Finding 1, each resample recomputes the five cross-demand outcome-pair τa coefficients and their mean within each maintainer profile, yielding confidence intervals for the means.

| Maintainer profile | Mean τa | 95% confidence interval |
| --- | ---: | --- |
| DeepSeek V4 Flash | +0.04 | [−0.11, +0.23] |
| HY3 | −0.02 | [−0.14, +0.15] |
| Kimi K2.7 Code | −0.07 | [−0.24, +0.04] |

Mean cross-demand τa is near zero for all profiles, with confidence-interval upper bounds of 0.23, 0.15, and 0.04, indicating low average agreement. Combined with high between-run ranking agreement, this supports demand-specific producer comparison and selection.

For Finding 2, we compare same-outcome producer rankings across maintainer profiles. Following the main text and Table A3, each resample uses common case weights to recompute τa for the three maintainer pairs and their mean.

| Outcome | Cross-maintainer mean τa | 95% confidence interval |
| --- | ---: | --- |
| Analysability score | +0.16 | [−0.17, +0.41] |
| Source reuse share | +0.46 | [+0.12, +0.71] |
| Reusability construction tokens | +0.49 | [+0.17, +0.71] |
| Testability construction tokens | −0.02 | [−0.21, +0.21] |

Reusability has the highest cross-maintainer mean τa (0.46 and 0.49), with both 95% confidence intervals supporting positive agreement.

### Response to Question 4

> Question 4: How should human practitioners use the benchmark or methodology to make critical decisions about which producer to use?

As Section 5 discusses, practitioners can identify their downstream maintenance work, select the corresponding panel, and compare producers under a matching maintainer profile. Cross-maintainer agreement indicates how consistently rankings transfer across downstream workers.

Multi-agent software engineering illustrates these distinct demands. MAGIS assigns code localization to a Repository Custodian (Tao et al., 2024); MetaGPT and AgentCoder assign test construction to a QA Engineer and test designer, respectively (Hong et al., 2024; Huang et al., 2024). These roles use upstream artifacts differently.

If downstream work emphasizes source understanding and behavioral analysis, practitioners can prioritize the producer's Analysability score. When building a new consumer around an existing artifact, source reuse share and construction tokens characterize the extent of existing-implementation use and construction cost, respectively. If downstream work emphasizes test construction, practitioners can compare Testability construction tokens. In each case, the goal is to select the producer whose code will be passed to the corresponding downstream role.

Practitioners can also evaluate candidate producers in their deployment environment, fixing the actual maintainer profile, downstream tasks, and budgets. CarryBench thus brings post-delivery maintenance outcomes into producer selection for the intended workflow.

### Response to Question 2

> Question 2: Considering the potential risk of biases in either case of including or excluding the same model as a maintainer of itself, why was it chosen to exclude? Could you provide a justification or comparison results if the self model was not excluded?

CarryBench evaluates maintainability through a fixed maintainer's downstream performance, requiring control of factors beyond the artifact itself. Models may prefer particular naming conventions, source organization, and implementation patterns. A model's own artifacts may better match its code-processing preferences, affecting downstream performance and confounding maintainability comparisons.

We exclude producer–maintainer identity pairs within each profile to reduce this potential bias and compare producers fairly. Cross-maintainer comparisons retain the seven producers evaluated by both profiles, ensuring a common candidate set.

### Response to Question 3

> Question 3: Were the downstream tasks for Reusability, Analysability, and Testability written by humans or AI? Was there any human validation in the process of selecting or validating these tasks?

The AI use statement discloses assistance in benchmark workflow development and inspection and individual downstream task construction, with author review of all AI-assisted work. Specifically:

Analysability uses automated construction from existing tests, without AI-generated questions. Under Section 3.3's common-pass design, questions derive from generation tests passed by all compared artifacts, with exams sampled by predefined rules. The original behavioral oracle supplies expected outputs and grading.

For Reusability and Testability, authors defined task objectives, behavioral scenarios, and evaluation requirements. AI helped implement these human-designed tasks as packages containing prompts, descriptions, and supporting files. The authors reviewed these materials for consistency with the task design and made the necessary corrections before evaluation. Thus, the substantive task design was determined by humans, while AI assisted in preparing the task materials under author review.

### References

Wei Tao, Yucheng Zhou, Yanlin Wang, Wenqiang Zhang, Hongyu Zhang, and Yu Cheng. [MAGIS: LLM-Based Multi-Agent Framework for GitHub Issue Resolution](https://papers.neurips.cc/paper_files/paper/2024/file/5d1f02132ef51602adf07000ca5b6138-Paper-Conference.pdf). In Advances in Neural Information Processing Systems, 2024.

Sirui Hong, Mingchen Zhuge, Jonathan Chen, Xiawu Zheng, Yuheng Cheng, Ceyao Zhang, Jinlin Wang, Zili Wang, Steven Ka Shing Yau, Zijuan Lin, Liyang Zhou, Chenyu Ran, Lingfeng Xiao, Chenglin Wu, and Jürgen Schmidhuber. [MetaGPT: Meta Programming for a Multi-Agent Collaborative Framework](https://proceedings.iclr.cc/paper_files/paper/2024/file/6507b115562bb0a305f1958ccc87355a-Paper-Conference.pdf). In International Conference on Learning Representations, 2024.

Dong Huang, Jie M. Zhang, Michael Luck, Qingwen Bu, Yuhao Qing, and Heming Cui. [AgentCoder: Multi-Agent-based Code Generation with Iterative Testing and Optimisation](https://arxiv.org/abs/2312.13010). arXiv preprint arXiv:2312.13010, 2024.
