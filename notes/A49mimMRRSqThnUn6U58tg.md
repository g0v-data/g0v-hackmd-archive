Dear Reviewer Q6kp,

Thank you for your helpful suggestions.

Weakness 1: The validation process for GPT-5-mini-assisted dataset reconstruction should be described in detail.

Thank you for your suggestion. The validation of GPT-5-mini-assisted dataset (i.e. INEP-EXEC) involved four annotators with experience in NLP and agent-memory tasks and two independent review rounds. In the first round, each annotator reviewed 200 non-overlapping samples. In the second round, all samples were reassigned to a different annotator, ensuring that every sample was independently reviewed by two annotators. Each sample was checked against its original BFCL example using three criteria:

Content fidelity: the rewritten dialogue preserves the original intent and constraints, and no action or argument is added, omitted, modified, duplicated, or reordered.
Decomposition validity: only meaningfully dependent actions are split, and the resulting action slices exactly recover the original action sequence.
Reference clarity: each implicit reference is unambiguous and recoverable from preceding turns.
The two independent reviews were compared before adjudication. Samples flagged by either reviewer were jointly re-examined, and corrected samples underwent an additional verification pass before acceptance.

Validation statistic	Value
Unique reconstructed samples	800
Number of annotators	4
First-round samples per annotator	200
Independent reviews per sample	2
Total sample-level reviews	1,600
Accepted without revision	780 (97.5%)
Accepted after manual correction	20 (2.5%)
Pre-adjudication exact agreement on the overall decision	775/800 (96.9%)
We will add the complete validation protocol, annotation criteria, error distribution, and aggregate statistics to the appendix.

Weakness 2: Uncertainty estimation should be included, especially when subsets are small.

Thank you for this suggestion. Our original evaluation reports single-run results, consistent with the experimental settings adopted in MemoryAgentBench [1] and Evo-Memory [2].. This choice also reflects a coverage–cost trade-off: EvoMemBench evaluates 15 baselines across six datasets, making repeated evaluation prohibitively expensive. Single-run evaluation allowed us to retain broad coverage at a feasible cost.

Considering your concern, we conducted additional repeated-run experiments on CROSSEP-EMB, where all six task categories contain fewer than 100 samples and are therefore particularly relevant to the concern about small subsets. Given the cost of repeating all 15 baselines, we selected representative methods spanning the major memory paradigms covered by EvoMemBench: DeepSeek-V3.2 as the memory-free baseline, BM25 as retrieval-augmented memory, Mem0 as general long-term memory, ReasoningBank as procedural long-term memory, and MemEvolve as meta-evolution memory. This design provides uncertainty estimates across diverse memory architectures while keeping the additional evaluation tractable. We ran each baseline three times and report the mean ± standard deviation below.

Method	Examine in Light	Pick & Place	Clean & Place	Cool & Place	Heat & Place	Pick Two & Place	Avg SR
DeepSeek-V3.2	75.4 ± 1.2	94.2 ± 1.2	55.2 ± 2.1	60.3 ± 2.2	58.0 ± 4.0	56.3 ± 4.6	66.6 ± 1.2
BM25	70.4 ± 2.0	97.8 ± 0.0	60.3 ± 2.1	61.7 ± 2.4	64.3 ± 3.1	72.3 ± 4.6	71.1 ± 1.1
Mem0	78.5 ± 2.1	87.7 ± 2.5	69.2 ± 3.1	60.1 ± 3.3	68.7 ± 4.2	54.1 ± 3.4	69.7 ± 1.3
ReasoningBank	78.0 ± 2.0	85.5 ± 3.5	78.6 ± 3.1	69.4 ± 2.0	61.7 ± 3.6	71.4 ± 3.4	74.1 ± 1.2
MemEvolve	60.2 ± 2.8	91.0 ± 3.3	67.5 ± 3.2	79.1 ± 4.0	74.7 ± 4.2	72.6 ± 4.2	74.2 ± 1.5
The three-run means remain close to the single-run results reported in the paper and preserve the overall comparative trends across memory paradigms. Although some fine-grained subsets exhibit greater variation because of their small sample sizes, the standard deviations of the aggregated average success rates are at most 1.5 percentage points. These results indicate that run-to-run variation has a limited effect on the overall comparisons and further support the robustness of our original findings.

[1] Yuanzhe Hu, Yu Wang, and Julian McAuley. Evaluating memory in llm agents via incremental multi-turn interactions. In ICLR, 2026.

[2] Tianxin Wei, Noveen Sachdeva, Benjamin Coleman, Zhankui He, Yuanchen Bei, Xuying Ning, Mengting Ai, Yunzhe Li, Jingrui He, Ed H. Chi, Chi Wang, Shuo Chen, Fernando Pereira, Wang Cheng Kang, and Derek Zhiyuan Cheng. Evo-memory: Benchmarking llm agent test-time learning with self-evolving memory. arXiv preprint arXiv:2511.20857, 2025. [Google DeepMind]