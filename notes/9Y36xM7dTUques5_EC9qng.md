# Reviewer CedU, 2（conf3）

Dear Reviewer CedU,

Thank you for your sincere comments and questions. We address them below.

### Response to Weakness 1 and Question 1

> Weakness 1: Most of the main findings are about rankings that don't agree, and the mean cross-task τ is close to 0. But the authors never rerun the same maintainer on the same artifact, and Reusability and Testability end up comparable only through token counts, so I can't tell whether this disagreement is a real difference or just noise.
>
> Question 1: Are there repeated runs of the same maintainer on the same artifact? What's the test-retest τ or ICC? If there are none, how do you distinguish the disagreement in Findings 1 and 2 from noise?

Our original evaluation prioritized coverage across producer models, maintainer profiles, and maintenance demands, given the cost of repository-level agent evaluation. To further assess the stability of our results, we conducted additional repeated evaluations using DeepSeek V4 Flash as a balance between capability and cost, while retaining all repository cases and all three maintenance demands. We held the Stage I artifacts, questions or tasks, prompts, tools, and budgets fixed, and performed two additional independent Stage II runs for each evaluation unit, resulting in three measurements per evaluation unit, including the original run.

The table below reports the mean ± sample standard deviation of each producer model's average performance across the three runs. Analysability score and source reuse share are percentages, with standard deviations in percentage points, while construction tokens are reported in thousands of tokens.

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

The three-run means remain close to the original results, with a maximum relative standard deviation of 1.78% across the reported metrics. To further assess consistency across runs, we also report single-measurement absolute-agreement ICC and Kendall's τ for producer rankings between runs.

| Outcome | ICC(A,1) | Original vs. repeat 1 τ | Original vs. repeat 2 τ | Repeat 1 vs. repeat 2 τ |
| --- | ---: | ---: | ---: | ---: |
| Analysability score | 0.9882 | 0.821 | 0.750 | 0.786 |
| Source reuse share | 0.9799 | 0.857 | 0.786 | 0.929 |
| Reusability construction tokens | 0.9977 | 1.000 | 1.000 | 1.000 |
| Testability construction tokens | 0.9968 | 0.929 | 0.929 | 0.857 |

ICC is computed at the artifact or downstream task-unit level, with construction tokens transformed using log(1 + tokens). Kendall's τ is computed over the eight producers' average-performance rankings. The ICC values of 0.9799–0.9977 and ranking correlations of 0.750–1.000 indicate high consistency in both measurements and producer rankings across repeated runs.

### Response to Weakness 2

> Weakness 2: Analysability gives the observer only 5 code inspections for 50 questions. Per Tables A2 and A11, Claude averages 10 source files and scores lowest, while GPT averages only 1.5 and scores highest. I suspect this mostly measures whether the code can be read within 5 calls, not how readable it is.

In our evaluation, the fixed source inspection budget allows us to compare Analysability under matched inspection effort, including the work of locating relevant logic, tracing cross-file dependencies, and understanding program behavior. The observer can search across multiple files within this budget and reuse the information obtained across all 50 questions.

The results in Table A11 suggest that the number of source files alone does not explain the differences in Analysability scores. GLM 5.2 has 8.308 source files on average and achieves scores of 89.2% and 86.9% under DeepSeek V4 Flash and HY3, respectively, while GLM 5.1 has only 2.231 files on average but achieves lower corresponding scores of 86.9% and 86.3%. The statix case illustrates this more directly: HY3 achieved 94% on GLM 5.2's eight-file implementation by inspecting three relevant source files within five calls, compared with 90% on GLM 5.1's single-file implementation. This example shows that an observer can locate and understand relevant behavior within the fixed inspection budget even when the implementation spans multiple files. The effort required therefore also depends on how the source is organized, rather than simply how many files it contains.

File count affects the search space and may also be associated with other aspects of source organization, such as naming and the distribution of logic. This is closely related to our lexical organization finding: the block covers identifier sharing and cross-file spread, import density, duplication, and local control structure, and examines their conditional association with Analysability.

### Response to Question 3

> Question 3: How was the 5-call inspection limit for Analysability chosen? With a larger budget, do the producer rankings and the Lexical organization association still hold?

Regarding the choice of inspection budget, our early comparison using DeepSeek V4 Flash showed that increasing the budget largely preserved the overall producer ordering and the lexical organization association. We therefore selected five calls for the main evaluation for cost and efficiency reasons, and extended this setting to HY3 and Kimi K2.7 Code.

The table below compares DeepSeek V4 Flash under budgets of 5, 10, and 20 calls. Parentheses indicate percentage-point changes relative to five calls.

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

As shown above, Analysability scores generally increase with the budget, while ranking changes are concentrated among producers with similar scores. Calculated from the displayed scores, Kendall's τa between the 5- and 10-call, 5- and 20-call, and 10- and 20-call rankings is 0.893, 0.893, and 0.929, respectively.

We also examined the lexical organization association under these budgets:

| Inspection budget | Partial R² | Change from 5 calls (percentage points) | q |
| --- | ---: | ---: | ---: |
| 5 | 13.80% | — | 0.0031 |
| 10 | 12.40% | −1.40 | 0.0075 |
| 20 | 10.30% | −3.50 | 0.0180 |

Partial R² decreases as the budget increases, while the association remains at q < 0.05 under all three settings.

### Response to Question 2

> Question 2: In Table A4, blocks with modest partial R² still get very small q values (e.g., the Analysability block has 13.80% with q = 0.0031, despite having 10 components and only 104 samples). Could you describe the permutation test and the effective sample size?

Thank you for raising this question. After carefully checking our analysis procedure and its description, we identified an inconsistency in Appendix A4.2. The actual analysis applies the specified transformations and standardization to the 10 components, aggregates them into a single block score, and adds that score to the baseline model. Thus, the full model adds only one predictor, consistent with the use of composite scores for Testability. However, Appendix A4.2 incorrectly describes these components as separate columns in the model. We apologize for this error and will correct the description in the revision to reflect the actual analysis.

Regarding the effective sample size, the unit of analysis is the artifact. The 50 behavioral questions are aggregated into one Analysability score per artifact, and the three maintainer profiles are analyzed separately. Excluding the producer–maintainer identity pair leaves 13 cases × 8 producers = 104 artifact-level observations per panel. Within each case, producers independently build implementations from empty workspaces, resulting in different internal structures and potentially different implementation languages. These implementations provide artifact-level variation, while their shared task structure is accounted for through case controls and within-case residual permutations.

For the permutation test, we first fit the baseline model and permute its residuals among the eight artifacts within each case. We then add the permuted residuals back to the original baseline fitted values, refit both the baseline model and the full model containing the block score, and calculate Partial R². The block score and the case, producer, and language labels remain fixed throughout this procedure, so each permutation evaluates the gain from adding the same score. The 13 within-case permutations form a joint permutation space of size $(8!)^{13}$, with each joint permutation yielding a statistic for the complete 104-artifact panel.

We use 20,000 random permutations and calculate the raw p-value as $p=(X+1)/(B+1)$, where $B=20{,}000$ and $X$ counts permutation statistics at least as large as the observed statistic. Benjamini–Hochberg (BH) correction is then applied over the complete set of candidate blocks for the same outcome and maintainer profile to obtain q.

# Reviewer vGFm, 3（conf3）

Dear Reviewer vGFm,

Thank you for your helpful suggestions. We address your concerns below.

### Response to Weakness 1 and Question 2

> Weakness 1: Testability covering just seven. Most tasks involve command-line programs, so it is unclear whether the findings generalize to larger, more complex software projects.
>
> Question 2: Could you evaluate Testability using bug detection or mutation testing, rather than only checking whether generated tests reproduce program behavior?

CarryBench evaluates the maintainability of agent-generated code through downstream maintenance tasks, beyond functional correctness. For Testability, we define a specific task in which a fixed tester constructs an executable black-box test suite for a generated program, with construction tokens measuring the cost of meeting the prescribed test-construction requirements.

A key consideration in this design is providing consistent test requirements and automatically obtainable ground truth across artifacts with different internal structures, implementation languages, and levels of functional correctness. Designing tests and expected results separately for each generated implementation would require implementation-specific manual work, limiting scalability to new producers and comparability across producers. Similarly, applying mutation testing to these heterogeneous implementations would require addressing the applicability of mutation operators, mutation validity, and the comparability of detection requirements. We therefore base the current task on prescribed behavioral scenarios and execution observations.

To support this design, the CLI provides a consistent interface across implementation languages. We specify behavioral scenarios and an observation schema at the case level, then automatically obtain trusted observations from each artifact's execution as its ground truth. The tester must accurately capture and represent the behavior of the current artifact, whose functional correctness may vary. This allows the same task protocol to be applied to artifacts from new producers without redesigning tasks or manually specifying expected outputs for each implementation, which is an important reason for prioritizing CLI programs.

The same design also provides a basis for expanding case coverage. New cases can define their behavioral scenarios and observation schemas under the existing protocol while reusing the controlled execution interface and acceptance mechanism based on trusted observations. Artifacts from new producers can then be evaluated directly using these case protocols. This extensibility also provides a path toward evaluating larger and more complex software projects。

The CLI interface also supports diverse testing requirements. For example, the Tokei task in Appendix A7.3 involves fixture construction, ignore and filtering rules, symbolic-link handling, two output surfaces, and relations between runs.

These test-construction activities are also closely related to bug detection and mutation testing. Detecting behavioral faults involves constructing inputs that exercise relevant behavior, executing the program, and reliably extracting observations to identify deviations against test criteria. Our task evaluates these activities and verifies their accuracy against artifact-specific ground truth, providing a consistent and automatically executable basis for comparing downstream test-construction costs.

### Response to Weakness 2

> Weakness 2: Some metrics may not reflect real maintainability. For example, the reuse score counts original code executed through the program interface, which does not necessarily mean the code is easy to reuse or extend. Similarly, Testability focuses on reproducing expected behavior rather than detecting actual bugs.

As described in Section 3.4, source reuse share and construction tokens are reported separately to characterize how the consumer builder completes a new task, capturing both the extent to which the existing implementation is used and the interaction cost of completing the task. Source reuse share measures the provenance of executed task-relevant code, including the use of existing functionality through the program interface as direct reuse. Construction tokens measure the cumulative interaction cost through the first accepted submission, capturing the work required to reuse or extend the program. Together, these outcomes distinguish cases where extensive use of the existing implementation is accompanied by substantial integration cost. A higher source reuse share therefore does not by itself imply easier reuse. We will clarify the complementary roles and interpretation of these metrics in the revision.

For Testability, constructing inputs, executing programs, and accurately capturing outputs and other execution effects are common software-testing activities also used in bug detection. Determining whether a behavioral fault exists typically involves comparing actual observations against test criteria, making reliable behavior capture an important part of the testing process. We operationalize this activity through executable black-box test suite construction: the tester must accurately capture and represent observations and relations between runs under prescribed behavioral scenarios, with construction tokens measuring the cost of completing this work. As discussed in our response to Weakness 1 and Question 2, trusted observations from the current artifact provide automatically obtainable ground truth, allowing consistent evaluation of test construction across implementations.

### Response to Question 1

> Question 1: How much of the reported reuse score comes from simply invoking the original program? Would the conclusions hold if these lines were excluded?

To address the contribution of artifact invocation, we separated generated-source lines reached through normal artifact invocation from reused source incorporated into the consumer, following the executed-source provenance definitions in Section 3.4 and Appendix A2.2. Based on artifact means for each producer, invocation contributes 99.90%, 99.90%, and 99.95% of source reuse share under DeepSeek V4 Flash, HY3, and Kimi K2.7 Code, respectively. These percentages refer to the reused-source portion of the score; the corresponding invocation contributions as a share of all executed task-relevant code are 79.03%, 78.33%, and 77.74%.

As discussed in our response to Weakness 1 and Question 2, the CLI provides a consistent interaction contract across implementations. Reusing functionality through library functions, APIs, or program interfaces is common in software engineering: a new consumer invokes an existing implementation and adds integration logic for new requirements without copying or reimplementing existing functionality. Our Reusability task supports this form of reuse through the CLI, so reuse predominantly occurs through artifact invocation. For example, the Rhit consumer in Appendix A7.2 invokes existing query functionality and adds normalization, merging, deduplication, sorting, and policy checks. The existing implementation thus contributes to a new case-specific workflow, motivating its inclusion as direct reuse in Section 3.4.

After excluding these source lines, only a small amount of reuse through source copying or adaptation remains, with most scores becoming zero. The remaining scores provide insufficient variation for meaningful producer-ranking and cross-maintainer agreement analyses. Excluding invocation lines would effectively restrict the metric to source copying and adaptation, which are uncommon in our current task. Since invoking existing functionality through program interfaces is itself a form of reuse, we retain these lines in the source reuse share metric.

# Reviewer ATVR, 2（conf2）
Dear Reviewer ATVR,

Thank you for your sincere comment. We address your concerns and questions below.

### Response to Weakness 1

> Weakness 1: Lack of a clear central finding and low statistical power. While the protocol is sound, the results and figures center around differences and variability rather than a cohesive unifying finding. The finding on tasks and how it affects producer rankings could be strengthened by repeat runs and bootstrap intervals on tau to establish the reliability of these differences. The stability of Reusability rankings is also based upon a partially statistically insignificant p-value (0.068) in the best-case scenario. Figure 3 further shows weak correlations between state cohesion and Analysability and the three other outcomes. It would be helpful for the authors to clarify the substantiality of the findings despite their heterogeneity and limited statistical significance and to provide higher-power analyses if possible.

CarryBench's central contribution is to operationalize the maintainability of agent-generated code through downstream evaluations that distinguish maintenance demands and condition comparisons on the maintainer profile. Our findings show that different maintenance demands yield different producer rankings and are associated with different source characteristics, with these patterns also varying across maintainer profiles.

Specifically, Findings 1 and 2 show that producer rankings differ across maintenance demands, while cross-maintainer agreement also varies by demand. Finding 4 further identifies different source-feature associations across maintenance demands and maintainer profiles. Together, these findings suggest that maintainability should be evaluated in the context of specific downstream work. We therefore report outcomes separately, allowing practitioners to select the panel corresponding to their anticipated maintenance tasks.

To further examine the reliability of these findings, we assess run-to-run variation through repeated evaluations with fixed artifacts and protocols. Bootstrap analysis of the original ranking associations is reported separately in our response to Question 1.

The repeated evaluation uses DeepSeek V4 Flash and retains all repository cases and all three maintenance demands. Excluding the producer–maintainer identity pair leaves eight producer models per panel. We fixed the Stage I artifacts, questions or tasks, prompts, tools, and budgets, and added two independent Stage II runs per evaluation unit, yielding three measurements including the original run. Each run contains 104 Analysability evaluations, 104 Reusability evaluations, and 96 Testability task runs covering 12 task instances over 7 independent cases. The following table reports single-measurement absolute-agreement ICC and Kendall's τ for producer rankings between runs.

| Outcome | ICC(A,1) | Original vs. repeat 1 τ | Original vs. repeat 2 τ | Repeat 1 vs. repeat 2 τ |
| --- | ---: | ---: | ---: | ---: |
| Analysability score | 0.9882 | 0.821 | 0.750 | 0.786 |
| Source reuse share | 0.9799 | 0.857 | 0.786 | 0.929 |
| Reusability construction tokens | 0.9977 | 1.000 | 1.000 | 1.000 |
| Testability construction tokens | 0.9968 | 0.929 | 0.929 | 0.857 |

The ICC values of 0.9799–0.9977 and ranking correlations of 0.750–1.000 indicate high repeatability of measurements and producer rankings for the same outcome. These additional evaluations assess run-to-run variation, while uncertainty in the original cross-demand and cross-maintainer comparisons is addressed separately under Question 1.

Regarding Finding 2, we distinguish the relative agreement pattern from statistical significance. All three cross-maintainer τ values for source reuse share are positive; two comparisons have p = 0.034 and 0.068, with the latter above the 0.05 threshold. All three coefficients for Reusability construction tokens are also positive, with a mean of 0.49. Thus, Finding 2 describes stronger cross-maintainer agreement for Reusability than for the other demands, without claiming statistical significance in every comparison.

Figure 3 examines whether state cohesion can substitute for direct downstream evaluation. The weak associations with mixed directions do not support using this static measure alone to infer downstream maintenance outcomes. Together, these findings support retaining the distinctions between maintenance demands and maintainer profiles when comparing producers for a target workflow.

### Response to Question 1

> Question 1: Is the disagreement across tasks and maintainers statistically significant, considering the modest differences? It would be helpful to show confidence intervals for tau values (for instance, bootstrapping).

To examine the uncertainty in the reported ranking associations, we performed a paired case bootstrap on the original evaluation data, using 2,000 resamples and percentile 95% confidence intervals. Each resample applies the same case weights to all producers and the outcomes or maintainer profiles being compared, recomputes producer-level outcomes, and calculates Kendall's τa. Construction tokens are ranked from low to high.

For Finding 1, we report the mean τa across five cross-demand outcome pairs within each maintainer profile. Each bootstrap resample recalculates the five coefficients and their mean, yielding a confidence interval for the mean.

| Maintainer profile | Mean τa | 95% confidence interval |
| --- | ---: | --- |
| DeepSeek V4 Flash | +0.04 | [−0.11, +0.23] |
| HY3 | −0.02 | [−0.14, +0.15] |
| Kimi K2.7 Code | −0.07 | [−0.24, +0.04] |

The mean cross-demand τa remains close to zero under all three maintainer profiles, with confidence-interval upper bounds of 0.23, 0.15, and 0.04, indicating low average ranking agreement across demands. Together with the high ranking agreement observed across repeated runs, these results support comparing and selecting producers separately for each maintenance demand.

For Finding 2, we compare producer rankings for the same outcome across maintainer profiles. Following the main text and Table A3, we report the mean τa across the three maintainer pairs. Each bootstrap resample uses common case weights to recalculate the three coefficients and their mean.

| Outcome | Cross-maintainer mean τa | 95% confidence interval |
| --- | ---: | --- |
| Analysability score | +0.16 | [−0.17, +0.41] |
| Source reuse share | +0.46 | [+0.12, +0.71] |
| Reusability construction tokens | +0.49 | [+0.17, +0.71] |
| Testability construction tokens | −0.02 | [−0.21, +0.21] |

The two Reusability outcomes have the highest cross-maintainer mean τa, at 0.46 and 0.49, and their 95% confidence intervals further support positive ranking agreement.

### Response to Question 4

> Question 4: How should human practitioners use the benchmark or methodology to make critical decisions about which producer to use?

As discussed in Section 5, practitioners can use CarryBench by first identifying their anticipated downstream maintenance work, selecting the corresponding evaluation panel, and comparing candidate producers under a matching maintainer profile. Agreement across maintainer profiles can then be examined to assess how consistently producer rankings transfer across downstream workers.

Multi-agent software engineering provides concrete examples. MAGIS assigns code localization to a Repository Custodian (Tao et al., 2024), while MetaGPT and AgentCoder assign test construction to a QA Engineer and a test designer, respectively (Hong et al., 2024; Huang et al., 2024). These roles work with upstream artifacts in different ways and therefore impose different maintenance demands.

If downstream work emphasizes source understanding and behavioral analysis, practitioners can prioritize the producer's Analysability score. If the goal is to build a new consumer around an existing artifact, source reuse share and construction tokens characterize the extent of existing-implementation use and construction cost, respectively. If downstream work emphasizes test construction, practitioners can compare Testability construction tokens. In each case, the selection concerns the producer whose code will be passed to the corresponding downstream role.

Practitioners can also apply the methodology in their own deployment environment by fixing the maintainer profile, downstream tasks, and budgets actually used, and evaluating artifacts from candidate producers under the same protocol. CarryBench thus incorporates maintenance outcomes after code delivery into producer selection, aligning the decision with the intended workflow.

### Response to Question 2

> Question 2: Considering the potential risk of biases in either case of including or excluding the same model as a maintainer of itself, why was it chosen to exclude? Could you provide a justification or comparison results if the self model was not excluded?

CarryBench evaluates code maintainability through the downstream performance of a fixed maintainer, making it important to control for factors beyond the artifact itself. Models may differ in their preferred naming conventions, source organization, and implementation patterns. When the same model serves as both producer and maintainer, its generated artifact may align more closely with its own code-processing preferences. Such alignment may affect downstream performance and consequently confound the evaluation of code maintainability.

We therefore exclude producer–maintainer identity pairs within each fixed maintainer profile to reduce this potential source of bias and enable fairer comparisons across producers. For cross-maintainer comparisons, we further retain the seven producers evaluated by both profiles, keeping the candidate set consistent.

### Response to Question 3

> Question 3: Were the downstream tasks for Reusability, Analysability, and Testability written by humans or AI? Was there any human validation in the process of selecting or validating these tasks?

The paper's AI use statement discloses generative AI assistance in benchmark workflow development and inspection, as well as in constructing individual downstream task instances, and states that the authors reviewed all AI-assisted work. The three downstream tasks were constructed as follows.

For Analysability, we use an automated construction process based on existing tests, without AI-generated questions. Following the common-pass design in Section 3.3, candidate questions are derived from generation tests that all compared artifacts pass, and exams are constructed using predefined sampling rules. Expected outputs and grading are provided by the original behavioral oracle.

For Reusability and Testability, the authors defined the task objectives, behavioral scenarios, and evaluation requirements. Generative AI assisted in implementing these human-designed tasks as concrete task packages, including prompts, task descriptions, and supporting files. The authors then reviewed these materials for consistency with the task design and made the necessary corrections before evaluation. Thus, the substantive task design was determined by humans, AI assisted with preparing the task materials, and the final task packages underwent author review.

### References

Wei Tao, Yucheng Zhou, Yanlin Wang, Wenqiang Zhang, Hongyu Zhang, and Yu Cheng. [MAGIS: LLM-Based Multi-Agent Framework for GitHub Issue Resolution](https://papers.neurips.cc/paper_files/paper/2024/file/5d1f02132ef51602adf07000ca5b6138-Paper-Conference.pdf). In Advances in Neural Information Processing Systems, 2024.

Sirui Hong, Mingchen Zhuge, Jonathan Chen, Xiawu Zheng, Yuheng Cheng, Ceyao Zhang, Jinlin Wang, Zili Wang, Steven Ka Shing Yau, Zijuan Lin, Liyang Zhou, Chenyu Ran, Lingfeng Xiao, Chenglin Wu, and Jürgen Schmidhuber. [MetaGPT: Meta Programming for a Multi-Agent Collaborative Framework](https://proceedings.iclr.cc/paper_files/paper/2024/file/6507b115562bb0a305f1958ccc87355a-Paper-Conference.pdf). In International Conference on Learning Representations, 2024.

Dong Huang, Jie M. Zhang, Michael Luck, Qingwen Bu, Yuhao Qing, and Heming Cui. [AgentCoder: Multi-Agent-based Code Generation with Iterative Testing and Optimisation](https://arxiv.org/abs/2312.13010). arXiv preprint arXiv:2312.13010, 2024.