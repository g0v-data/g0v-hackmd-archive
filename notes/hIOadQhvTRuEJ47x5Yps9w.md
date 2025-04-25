# DeepSeek-R1：通过强化学习激励大语言模型的推理能力

DeepSeek-AI  

research@deepseek.com

# 摘要

![](images/ff7821aa41ec4ddf51146718d7ddca7da6a52462d5e5b1246ed6db1786f727f7.jpg)

*图1 | DeepSeek-R1基准测试性能表现*

我们推出第一代推理模型DeepSeek-R1-Zero和DeepSeek-R1。其中DeepSeek-R1-Zero是通过大规模强化学习（RL）直接训练而成，未经过监督微调（SFT）的预训练阶段，却展现出卓越的推理能力。通过强化学习，该模型自然涌现出众多强大而有趣的推理行为，但也面临可读性差、语言混杂等挑战。为解决这些问题并进一步提升推理性能，我们开发了采用多阶段训练并在强化学习前引入冷启动数据的DeepSeek-R1。该模型在推理任务上达到了与OpenAI-ol-1217相当的水平。为支持研究社区，我们开源了DeepSeek-R1-Zero、DeepSeek-R1以及基于Qwen和Llama从DeepSeek-R1蒸馏得到的六个稠密模型（1.5B、7B、8B、14B、32B、70B）。

# 3 引言

1.1 主要贡献 4
1.2 评估结果概要 4

# 2 方法 5

2.1 概述 5
2.2 DeepSeek-R1-Zero：基础模型的强化学习 5
2.2.1 强化学习算法 5
2.2.2 奖励建模 6
2.2.3 训练模板 6
2.2.4 DeepSeek-R1-Zero的性能、自我进化过程与顿悟时刻 6
2.3 DeepSeek-R1：冷启动强化学习 9
2.3.1 冷启动 9
2.3.2 面向推理的强化学习 10
2.3.3 拒绝采样与监督微调 10
2.3.4 全场景强化学习 11
蒸馏：为小模型赋予推理能力 11

# 3 实验11

3.1 DeepSeek-R1评估 13
3.2 蒸馏模型评估 14

# 14 讨论

4.1 蒸馏与强化学习对比 14
4.2 未成功的尝试 15

# 5 结论、局限性与未来工作 16

A 贡献与致谢 20

# 1. 引言

近年来，大型语言模型（LLMs）正经历快速迭代与演进，逐步缩小与通用人工智能（AGI）的差距。

后训练阶段已成为完整训练流程中的重要组成部分。研究表明，该阶段能以相对预训练较少的计算资源，有效提升推理任务准确率、实现社会价值观对齐并适应用户偏好。在推理能力方面，OpenAI的o1系列模型首次通过增加思维链推理长度实现了推理时扩展，在数学、编程和科学推理等任务中取得显著提升。但如何实现有效的测试时扩展仍是学界待解难题。现有研究探索了多种方法，包括基于过程的奖励模型、强化学习以及蒙特卡洛树搜索和束搜索等算法，但尚未出现能达到OpenAI o1系列模型通用推理性能的方案。

本文首次尝试采用纯强化学习（RL）方法来提升语言模型的推理能力。我们的目标是探索大型语言模型（LLMs）在无监督数据条件下发展推理能力的潜力，重点关注其通过纯强化学习过程实现的自我进化。具体而言，我们以DeepSeek-V3-Base作为基础模型，采用GRPO（Shao et al., 2024）作为强化学习框架来提升模型的推理性能。在训练过程中，DeepSeek-R1-Zero自然涌现出大量强大且有趣的推理行为。经过数千步强化学习训练后，DeepSeek-R1-Zero在推理基准测试中展现出卓越性能。例如，在AIME 2024测试中的pass $@1$分数从$15.6\%$提升至$71.0\%$，采用多数投票策略后分数进一步提高至$86.7\%$，达到了与OpenAI-o1-0912相当的水平。

然而，DeepSeek-R1-Zero面临着可读性差和语言混杂等挑战。为解决这些问题并进一步提升推理性能，我们引入了DeepSeek-R1，该方法结合少量冷启动数据（cold-start data）和多阶段训练流程。具体而言，我们首先收集数千条冷启动数据对DeepSeek-V3-Base模型进行微调。随后，我们实施类似DeepSeek-R1-Zero的推理导向强化学习。当强化学习过程接近收敛时，我们通过对强化学习检查点进行拒绝采样生成新的监督微调（SFT）数据，并结合DeepSeek-V3在写作、事实问答和自我认知等领域的监督数据，重新训练DeepSeek-V3-Base模型。使用新数据微调后，该检查点会经历额外的强化学习过程，该过程考虑了所有场景的提示词。经过这些步骤，我们最终获得称为DeepSeek-R1的检查点，其性能达到了与OpenAI-o1-1217相当的水平。

我们进一步探索了从DeepSeek-R1到更小稠密模型的蒸馏技术。以Qwen2.5-32B作为基础模型，直接采用DeepSeek-R1进行蒸馏的效果优于在其上应用强化学习。这表明更大基础模型所发现的推理模式对提升推理能力至关重要。我们开源了蒸馏后的Qwen和Llama系列模型。值得注意的是，我们蒸馏得到的14B模型大幅超越了当前最先进的开源模型QwQ-32B-Preview，而蒸馏后的32B和70B模型则在稠密模型的推理基准测试中创造了新纪录。

## 1.2. 评估结果总结

· 推理任务：(1) DeepSeek-R1在AIME 2024上取得79.8%的Pass@1分数，小幅超越OpenAI-o1-1217。在MATH-500测试中，它以97.3%的优异表现与OpenAI-ol-1217持平，并显著优于其他模型。(2) 在代码相关任务上，DeepSeek-R1展现出竞赛级编码能力——其Codeforces平台Elo评分达2029分，超越该平台96.3%的人类参赛者。对于工程实践类任务，该模型表现略优于DeepSeek-V3，可为开发者提供实际工作支持。

· 知识能力：在MMLU、MMLU-Pro和GPQA Diamond等基准测试中，DeepSeek-R1表现卓越，以90.8%的MMLU得分、84.0%的MMLU-Pro得分和71.5%的GPQA Diamond得分显著超越DeepSeek-V3。虽然在这些基准上略逊于OpenAI-ol-1217，但DeepSeek-R1超越了其他闭源模型，展现了其在教育类任务中的竞争优势。在事实性基准测试SimpleQA中，DeepSeek-R1优于DeepSeek-V3，证明了其处理事实性查询的能力。类似趋势也体现在OpenAI-o1在该基准上超越4o的表现中。

· 其他能力：DeepSeek-R1在创意写作、通用问答、文本编辑、摘要生成等多样化任务中同样表现优异。该模型在AlpacaEval 2.0基准测试中获得87.6%的长度控制胜率，在ArenaHard基准上达到92.3%的胜率，充分展现其处理非应试类查询的智能水平。此外，DeepSeek-R1在需要长文本理解的任务中表现突出，在长文本基准测试上显著超越DeepSeek-V3。

# 后训练：基于基础模型的大规模强化学习

· 我们直接在基础模型上应用强化学习（RL），无需依赖监督微调（SFT）作为前置步骤。这种方法使模型能够通过思维链（CoT）探索复杂问题的解决方案，最终开发出DeepSeek-R1-Zero。该模型展现出自我验证、反思和生成长链思维等能力，为研究社区树立了重要里程碑。值得注意的是，这是首个公开验证大语言模型推理能力可完全通过${\mathrm{RL}}$激励实现、无需SFT的研究。这一突破为该领域的未来发展开辟了新路径。

· 我们介绍了开发DeepSeek-R1的完整流程。该流程包含两个RL阶段（用于发现更优推理模式并与人类偏好对齐）以及两个SFT阶段（作为模型推理与非推理能力的种子）。我们相信这一流程将通过创建更优质模型推动行业发展。

# 蒸馏：小模型亦可强大

· 我们证明了大模型的推理模式可以被蒸馏到小模型中，相比在小模型上通过强化学习发现的推理模式能获得更好的性能。开源的DeepSeek-R1及其API将有助于研究社区未来蒸馏出更优秀的小模型。
· 利用DeepSeek-R1生成的推理数据，我们对研究社区广泛使用的多个稠密模型进行了微调。评估结果表明，经过蒸馏的小型稠密模型在基准测试中表现优异。DeepSeekR1-Distill-Qwen-7B在AIME 2024上达到55.5%，超越QwQ-32B-Preview。此外，DeepSeek-R1-Distill-Qwen-32B在AIME 2024上得分72.6%，在MATH-500上94.3%，在LiveCodeBench上57.2%。这些结果显著超越了之前的开源模型，并与ol-mini相当。我们向社区开源了基于Qwen2.5和Llama3系列蒸馏得到的1.5B、7B、8B、14B、32B和70B检查点。

# 2. 方法

## 2.1. 概述

先前的研究严重依赖大量监督数据来提升模型性能。在本研究中，我们证明即使不使用监督微调（SFT）作为冷启动，通过大规模强化学习（RL）也能显著提升推理能力。此外，加入少量冷启动数据可进一步优化性能。后续章节我们将展示：（1）DeepSeek-R1-Zero——直接在基础模型上应用RL而无需任何SFT数据；（2）DeepSeek-R1——从经过数千条长思维链（CoT）样本微调的检查点开始应用RL；（3）将DeepSeek-R1的推理能力蒸馏至小型稠密模型。

## 2.2. DeepSeek-R1-Zero：基于基础模型的强化学习

强化学习在推理任务中已展现出显著成效，这在我们先前的研究中得到了验证。然而这些研究高度依赖监督数据，而此类数据的收集往往耗时费力。本节我们将探索大语言模型在完全无监督数据条件下发展推理能力的可能性，重点关注其通过纯强化学习过程实现自我进化的潜力。我们首先简要概述强化学习算法框架，随后展示部分令人振奋的研究成果，期望能为学界提供有价值的洞见。

### 2.2.1. 强化学习算法

群体相对策略优化
为节省$\scriptstyle\mathrm{RL}$训练成本，我们采用群体相对策略优化（GRPO），该方法省去了通常与策略模型规模相当的评判模型，转而通过群体得分估算基线值。具体而言，对于每个问题$q$，GRPO从旧策略$\pi_{\theta_{o l d}}$采样一组输出$\{o_{1},o_{2},\cdots,o_{G}\}$，随后通过最大化以下目标函数来优化策略模型$\scriptstyle{\pi_{\theta}}$：

$$ 
\begin{array}{l}{\displaystyle\mathcal{I}_{G R P O}(\theta)=\mathbb{E}[q\sim P(Q),\{o_{i}\}_{i=1}^{G}\sim\pi_{\theta_{o l d}}(O|q)]}\\ {\displaystyle\frac{1}{G}\sum_{i=1}^{G}\left(\operatorname*{min}\left(\frac{\pi_{\theta}(o_{i}|q)}{\pi_{\theta_{o l d}}(o_{i}|q)}A_{i},\mathrm{clip}\left(\frac{\pi_{\theta}(o_{i}|q)}{\pi_{\theta_{o l d}}(o_{i}|q)},1-\varepsilon,1+\varepsilon\right)A_{i}\right)-\beta\mathbb{D}_{K L}\left(\pi_{\theta}||\pi_{r e f}\right)\right),}\end{array}
 $$

$$ 
\mathbb{D}_{K L}\left(\pi_{\theta}||\pi_{r e f}\right)=\frac{\pi_{r e f}(o_{i}|q)}{\pi_{\theta}(o_{i}|q)}-\log\frac{\pi_{r e f}(o_{i}|q)}{\pi_{\theta}(o_{i}|q)}-1,
 $$

其中$\varepsilon$和$\beta$为超参数，$A_{i}$表示优势函数，通过计算每组输出对应的奖励集合$\{r_{1},r_{2},\cdots,r_{G}\}$得出：

$$ 
A_{i}={\frac{r_{i}-\mathrm{m}e a n(\{r_{1},r_{2},\cdot\cdot\cdot,r_{G}\})}{s t d(\{r_{1},r_{2},\cdot\cdot\cdot,r_{G}\})}}.
 $$

用户与助手之间的对话。用户提出问题，助手负责解答。助手首先在脑海中思考推理过程，然后向用户提供答案。推理过程和答案分别包含在<think></think>和<answer></answer>标签中，即<think>此处为推理过程</think><answer>此处为答案</answer>。用户：提示。助手：

### 2.2.2. 奖励建模

奖励是训练信号的来源，决定了强化学习的优化方向。为训练DeepSeek-R1-Zero，我们采用基于规则的奖励系统，主要包括两类奖励：

· 准确性奖励：准确性奖励模型评估回答是否正确。例如，对于结果确定的数学问题，模型需以指定格式（如方框内）提供最终答案，从而实现基于规则的正确性验证。类似地，对于LeetCode问题，可通过编译器基于预定义测试用例生成反馈。

· 格式奖励：除准确性奖励模型外，我们还采用格式奖励模型，强制模型将思考过程置于`<think>`和`</think>`标签之间。

在开发DeepSeek-R1-Zero过程中，我们未采用结果或过程神经奖励模型（neural reward model），因为发现神经奖励模型在大规模强化学习过程中可能出现奖励破解（reward hacking）问题。此外，重新训练奖励模型需要额外计算资源，还会使整个训练流程复杂化。

### 2.2.3. 训练模板

为训练DeepSeek-R1-Zero，我们首先设计了一个简洁的模板来引导基础模型遵循指定指令。如表1所示，该模板要求DeepSeek-R1-Zero先生成推理过程，再输出最终答案。我们刻意将约束条件仅限定于这种结构框架，避免引入任何内容层面的偏向性（例如强制要求反思性推理或推崇特定解题策略），以确保能准确观察模型在强化学习过程中的自然演进。

### 2.2.4. DeepSeek-Ri-Zero的性能表现、自我进化过程与顿悟时刻

DeepSeek-R1-Zero的性能表现 图2展示了DeepSeek-R1-Zero在AIME 2024基准测试中随RL训练进程的性能变化轨迹。如图所示，随着RL训练的推进，DeepSeek-R1-Zero展现出稳定而持续的提升。值得注意的是，其AIME 2024平均通过率$@1$分数从初始的$15.6\%$显著跃升至$71.0\%$，达到与OpenAI-ol-0912相当的水平。这一显著进步凸显了我们RL算法在持续优化模型性能方面的有效性。

<html><body><table><tr><td rowspan="2">Model</td><td colspan="2">AIME 2024</td><td rowspan="2">MATH-500</td><td rowspan="2">GPQA Diamond</td><td rowspan="2">LiveCode Bench</td><td rowspan="2">CodeForces</td></tr><tr><td>pass@1</td><td>cons@64</td></tr><tr><td>OpenAI-o1-mini</td><td>63.6</td><td>80.0</td><td>pass@1</td><td>60.0 pass@1</td><td>53.8 pass@1</td><td>rating</td></tr><tr><td>OpenAI-o1-0912</td><td>74.4</td><td>83.3</td><td>90.0 94.8</td><td>77.3</td><td>63.4</td><td>1820 1843</td></tr><tr><td>DeepSeek-R1-Zero</td><td>71.0</td><td>86.7</td><td>95.9</td><td>73.3</td><td>50.0</td><td>1444</td></tr></table></body></html>

*表2 | DeepSeek-R1-Zero与OpenAI o1模型在推理相关基准测试中的对比*

![](images/ab45d6d4a18a16de622b590f33e484e3295ea072cdb7d319a68336ec13bc2f61.jpg)

*图2| DeepSeek-R1-Zero在训练过程中的AIME准确率。针对每个问题，我们采样16个回答并计算总体平均准确率以确保评估稳定性。*

DeepSeek-R1-Zero无需任何监督微调数据即可获得强大的推理能力。这一显著成就突显了该模型仅通过强化学习就能有效学习和泛化的能力。此外，通过应用多数投票（majority voting）方法可进一步提升DeepSeek-R1-Zero的性能表现。例如，在AIME基准测试中使用多数投票时，其性能从71.0%提升至86.7%，从而超越了OpenAI-o1-0912的表现。DeepSeek-R1-Zero无论是否采用多数投票都能实现如此具有竞争力的性能，这充分彰显了其强大的基础能力以及在推理任务中持续进步的潜力。

DeepSeek-R1-Zero的自我进化过程
DeepSeek-R1-Zero的自我进化过程生动展示了强化学习如何驱动模型自主提升推理能力。通过直接从基础模型启动强化学习，我们能够排除监督微调阶段的影响，密切追踪模型的演进轨迹。这种方法清晰地展现了模型随时间推移的进化过程，特别是在处理复杂推理任务方面的能力提升。

如图3所示，DeepSeek-R1-Zero的思考时长在整个训练过程中持续改善。这种改进并非来自外部调整，而是模型内在的发展结果。通过利用扩展的测试时计算（从生成数百到数千个推理标记不等），DeepSeek-R1-Zero自然获得了解决日益复杂推理任务的能力，使其能够更深入地探索和完善思维过程。

![](images/ccd60793cd5609860810dbcc42dc8670b9cc82e28401d9399ee0218f814f5a03.jpg)

*图3| DeepSeek-R1-Zero在强化学习过程中对训练集的平均响应长度。该模型通过自然学习，以更长的思考时间来解决推理任务。*

这种自我进化最显著的特点之一，是随着测试时计算的增加而涌现出的复杂行为。诸如反思（模型重新审视和评估其先前步骤）以及探索替代性解题方法等行为，都是自发产生的。这些行为并非显式编程实现，而是模型与强化学习环境交互的自然结果。这种自发发展显著增强了DeepSeek-R1-Zero的推理能力，使其能够以更高效率和准确度应对更具挑战性的任务。

DeepSeek-R1-Zero的顿悟时刻  
在DeepSeek-R1-Zero训练过程中观察到一个特别有趣的现象——"顿悟时刻"（aha moment）。如表3所示，这一时刻出现在模型的中间版本阶段。在此阶段，DeepSeek-R1-Zero学会了通过重新评估初始解题思路来为问题分配更多思考时间。这种行为不仅证明了模型不断增强的推理能力，更成为强化学习能产生意外而精妙结果的生动例证。

这一时刻不仅是模型的"顿悟时刻"，对观察其行为的研究人员而言同样如此。它彰显了强化学习的强大与美妙：我们无需明确教导模型如何解决问题，只需提供恰当的激励，它就能自主发展出高级的问题解决策略。"顿悟时刻"有力地提醒着我们，强化学习具有释放人工智能系统新智能层级的潜力，为未来开发更自主、更具适应性的模型铺平了道路。

问题：若$a>1$，则方程${\sqrt{a-{\sqrt{a+x}}}}=x$的所有实数解之和等于  
回答：<思考>
要解方程${\sqrt{a-{\sqrt{a+x}}}}=x$，我们首先对两边平方：
$\left({\sqrt{a-{\sqrt{a+x}}}}\right)^{2}=x^{2}\implies a-{\sqrt{a+x}}=x^{2}.$
重新整理以分离内部平方根项：
$(a-x^{2})^{2}=a+x\implies a^{2}-2a x^{2}+x^{4}=a+x\implies x^{4}-2a x^{2}-x+(a^{2}-a)=0$ 等等，这里出现了关键转折点。
让我们逐步重新审视这个推导过程，确认是否能正确求出解的和...
初始方程为：
${\sqrt{a-{\sqrt{a+x}}}}=x$
首先对两边平方：
$a-{\sqrt{a+x}}=x^{2}\implies{\sqrt{a+x}}=a-x^{2}$
接下来可对两边再次平方，处理方程：

DeepSeek-R1-Zero的缺陷 尽管DeepSeek-R1-Zero展现出强大的推理能力，并能自主发展出意料之外且强有力的推理行为，但它仍面临若干问题。例如，该模型在可读性差、语言混杂等挑战上表现欠佳。为了使推理过程更具可读性并与开放社区共享，我们探索了DeepSeek-R1方法——这是一种利用人类友好冷启动数据（human-friendly cold-start data）进行强化学习的技术。

## 2.3. DeepSeek-R1：冷启动强化学习

受到DeepSeek-R1-Zero优异表现的启发，我们自然产生两个问题：1）通过引入少量高质量数据作为冷启动（cold start），能否进一步提升推理性能或加速收敛？2）如何训练出既能生成清晰连贯的思维链（Chains of Thought，CoT），又具备强大通用能力的用户友好型模型？为解决这些问题，我们设计了训练DeepSeek-R1的流程管道。该管道包含以下四个主要阶段。

### 2.3.1. 冷启动

与DeepSeek-R1-Zero不同，为避免基础模型在强化学习训练初期出现不稳定的冷启动阶段，我们为DeepSeek-R1构建并收集了小批量长链思维（CoT）数据对模型进行微调，作为初始强化学习执行器。为收集此类数据，我们探索了多种方法：使用带有长链思维示例的小样本提示、直接提示模型生成包含反思与验证的详细答案、收集DeepSeek-R1-Zero的可读格式输出，以及通过人工标注员进行后处理优化结果。

在本工作中，我们收集了数千条冷启动数据对DeepSeek-V3-Base进行微调，作为强化学习的起点。与DeepSeek-R1-Zero相比，冷启动数据的优势包括：

· 可读性：DeepSeek-R1-Zero的一个关键局限是其内容通常不适合阅读。响应可能混杂多种语言或缺乏Markdown格式来为用户突出答案。相比之下，在为DeepSeek-R1创建冷启动数据时，我们设计了包含每项响应末尾摘要的可读模式，并过滤掉不便于阅读的响应。此处我们将输出格式定义为I special_tokenl<推理过程> I special_tokenl<摘要>，其中推理过程是查询的思维链（CoT），摘要用于总结推理结果。

· 潜力：通过结合人类先验知识精心设计冷启动数据模式，我们观察到其性能优于DeepSeek-R1-Zero。我们认为迭代训练是培养推理模型的更优方式。

### 2.3.2. 面向推理的强化学习

在对DeepSeek-V3-Base进行冷启动数据微调后，我们采用了与DeepSeek-R1-Zero相同的大规模强化学习训练流程。该阶段主要聚焦于增强模型的推理能力，特别是在编码、数学、科学和逻辑推理等具有明确定义解决方案的推理密集型任务上。训练过程中，我们观察到思维链（CoT）经常出现语言混杂现象，尤其是当强化学习提示涉及多种语言时。为缓解语言混杂问题，我们在强化学习训练中引入了语言一致性奖励机制，该奖励通过计算思维链中目标语言词汇的占比来实现。消融实验表明，虽然这种对齐会导致模型性能轻微下降，但该奖励机制更符合人类偏好，使输出更具可读性。最终，我们将推理任务准确率与语言一致性奖励直接相加形成最终奖励信号，并对微调后的模型持续进行强化学习训练直至其在推理任务上达到收敛。

### 2.3.3. 拒绝采样与监督微调

当面向推理的强化学习收敛时，我们利用最终检查点收集监督微调（SFT）数据用于下一轮训练。与初始冷启动数据主要聚焦推理不同，本阶段整合了其他领域数据以增强模型在写作、角色扮演等通用任务上的能力。具体而言，我们按以下方式生成数据并微调模型。

推理数据 我们精选推理提示词，通过从上述RL训练检查点进行拒绝采样来生成推理轨迹。前一阶段仅包含可通过基于规则奖励评估的数据，而本阶段通过引入额外数据扩展数据集，其中部分数据通过将标准答案和模型预测输入DeepSeek-V3进行判定的生成式奖励模型来评估。此外，由于模型输出有时存在混乱可读性差的问题，我们过滤了语言混杂的思维链、冗长段落和代码块。针对每个提示词，我们对多个响应进行采样并仅保留正确答案。最终我们收集了约60万条推理相关训练样本。

非推理数据 对于写作、事实问答、自我认知和翻译等非推理类数据，我们采用DeepSeek-V3的流程并复用其部分监督微调数据集。针对特定非推理任务，我们会调用DeepSeek-V3在回答问题前先生成潜在思维链。但对于"你好"等简单查询，则不会提供思维链响应。最终我们收集了约20万条与推理无关的训练样本。

我们使用上述约80万样本的精选数据集对DeepSeek-V3-Base进行了两个周期的微调。

### 2.3.4. 面向全场景的强化学习

为进一步使模型与人类偏好对齐，我们实施了第二阶段强化学习，旨在提升模型的有用性和无害性，同时优化其推理能力。具体而言，我们采用奖励信号与多样化提示分布相结合的方式进行训练。对于推理数据，我们遵循DeepSeek-R1-Zero提出的方法论，通过基于规则的奖励机制来指导数学、代码和逻辑推理领域的学习过程。针对通用数据，我们采用奖励模型来捕捉复杂细微场景中的人类偏好。基于DeepSeek-V3的训练流程，我们采用了类似的偏好对分布和训练提示策略。在有用性优化方面，我们仅关注最终总结部分，确保评估聚焦于回答对用户的实用性和相关性，同时最小化对底层推理过程的干扰。在无害性优化方面，我们评估模型的完整输出（包括推理过程和总结），以识别并消除生成过程中可能出现的风险、偏见或有害内容。最终，通过整合奖励信号与多样化数据分布，我们成功训练出在保持卓越推理能力的同时，兼具高度有用性和无害性的模型。

## 2.4. 蒸馏：赋能小模型推理能力

为使更高效的小型模型具备类似DeepSeek-R1的推理能力，我们使用DeepSeek-R1精选的80万样本直接对Qwen和Llama等开源模型进行微调（详见$\S2.3.3$节）。研究发现，这种简单的蒸馏方法能显著提升小型模型的推理能力。本研究所用基础模型包括Qwen2.5-Math-1.5B、Qwen2.5-Math-7B、Qwen2.5-14B、Qwen2.5-32B、Llama-3.1-8B以及Llama-3.3-70B-Instruct。选择Llama-3.3版本是因为其推理能力略优于Llama-3.1版本。

对于蒸馏模型，我们仅采用监督微调（SFT）而不包含强化学习（RL）阶段，尽管引入RL能显著提升模型性能。本研究的主要目标是验证蒸馏技术的有效性，将RL阶段的探索留给更广泛的研究社区。

# 3. 实验

基准测试 我们在MMLU、MMLU-Redux、MMLU-Pro、C-Eval、CMMLU、IFEval、FRAMES、GPQA Diamond、SimpleQA、C-SimpleQA、SWE-Bench Verified、Aider 1、LiveCodeBench（2024-08至2025-01）、Codeforces²、中国高中数学奥林匹克（CNMO 2024）³以及美国数学邀请赛2024（AIME 2024）等基准上评估模型性能。除标准基准外，我们还采用大语言模型作为评判者，对开放生成任务进行评估。具体而言，我们遵循AlpacaEval 2.0和Arena-Hard的原始配置，使用GPT-4-Turbo-1106进行成对比较评估。为避免长度偏差，此处仅将最终摘要输入评估系统。对于蒸馏模型，我们报告了在AIME 2024、MATH-500、GPQA Diamond、Codeforces和LiveCodeBench上的代表性结果。

评估提示 遵循DeepSeek-V3的设置，我们使用simpleevals框架提供的提示词对MMLU、DROP、GPQA Diamond和SimpleQA等标准基准进行评估。针对MMLU-Redux，我们采用零样本设置下的Zero-Eval提示格式（Lin, 2024）。对于MMLU-Pro、C-Eval和CLUE-WSC，由于原始提示为少样本形式，我们将其微调为零样本设置——少样本中的思维链（CoT）可能影响DeepSeek-R1的性能表现。其余数据集均遵循创建者提供的原始评估协议与默认提示。在代码与数学基准方面，HumanEval-Mul数据集涵盖八种主流编程语言（Python、Java、C++、C#、JavaScript、TypeScript、PHP和Bash）。LiveCodeBench的模型性能采用思维链格式评估，数据采集时间为2024年8月至2025年1月。Codeforces数据集通过10场Div.2竞赛题目及专家编写的测试用例进行评估，随后计算预期评级与参赛者百分比。SWE-Bench验证结果通过无代理框架（Xia et al., 2024）获取。AIDER相关基准采用"差异格式"进行测量。DeepSeek-R1在各基准测试中的输出长度上限设定为32,768个标记。

基线模型 我们针对多个强基线模型进行了全面评估，包括DeepSeek-V3、Claude-Sonnet-3.5-1022、GPT-4o-0513、OpenAI-o1-mini以及OpenAI-o1-1217。由于OpenAI-ol-1217的API在中国大陆难以访问，其性能数据基于官方报告。对于蒸馏模型，我们还对比了开源模型QwQ-32B-Preview（Qwen, 2024a）。

评估设置 所有模型的最大生成长度均设为32,768个标记。我们发现使用贪心解码评估长文本推理模型会导致更高的重复率和不同检查点间的显著波动。因此默认采用pass@k评估方法（Chen et al., 2021），并使用非零温度报告pass@1结果。具体而言，我们采用0.6的采样温度和0.95的top p值，为每个问题生成k个响应（通常在4至64之间，取决于测试集规模），pass@1的计算公式为

$$ 
\mathrm{pass}@1=\frac{1}{k}\sum_{i=1}^{k}p_{i},
 $$

其中$p_{i}$表示第$i$个响应的正确性。该方法能提供更可靠的性能评估。对于AIME 2024，我们还报告了基于64个样本的共识（多数表决）结果（cons@64）。

## 3.1. DeepSeek-R1 评估

<html><body><table><tr><td>Benchmark (Metric)</td><td>Sonnet-1022</td><td>Claude-3.5- GPT-4o DeepSeek|OpenAI OpenAI|DeepSeek 0513</td><td>V3</td><td>ol-mini o1-1217</td><td></td><td>R1</td></tr><tr><td></td><td>Architecture # Activated Params # Total Params</td><td></td><td></td><td>MoE 37B 671B</td><td></td><td></td><td>MoE 37B</td></tr><tr><td>English</td><td>MMLU (Pass@1) MMLU-Redux (EM) MMLU-Pro (EM) DROP (3-shot F1) IF-Eval (Prompt Strict) GPQA Diamond (Pass@1) SimpleQA (Correct)</td><td>88.3 88.9 78.0 88.3 86.5 65.0 28.4</td><td>87.2 88.0 72.6 83.7 84.3 49.9 38.2</td><td>88.5 89.1 75.9 91.6 86.1 59.1 24.9</td><td>85.2 86.7 80.3 83.9 84.8 60.0 7.0</td><td>91.8 90.2 75.7</td><td>671B 90.8 92.9 84.0 92.2 83.3 71.5</td></tr><tr><td>Code</td><td>FRAMES (Acc.) AlpacaEval2.0 (LC-winrate) ArenaHard (GPT-4-1106) LiveCodeBench (Pass@1-COT) Codeforces (Percentile)</td><td>72.5 52.0 85.2 38.9</td><td>80.5 51.1 80.4 32.9</td><td>73.3 70.0 85.5 36.2</td><td>76.9 57.8 92.0 53.8</td><td>47.0 63.4</td><td>30.1 82.5 87.6 92.3 65.9</td></tr><tr><td>Math</td><td>Codeforces (Rating) SWE Verified (Resolved) Aider-Polyglot (Acc.) AIME 2024 (Pass@1)</td><td>20.3 717 50.8 45.3 16.0</td><td>23.6 759 38.8 16.0 9.3</td><td>58.7 1134 42.0 49.6 39.2</td><td>93.4 1820 41.6 32.9 63.6</td><td>96.6 2061 48.9 61.7 79.2</td><td>96.3 2029 49.2 53.3 79.8</td></tr><tr><td>Chinese C-Eval (EM)</td><td>MATH-500 (Pass@1) CNMO 2024 (Pass@1) CLUEWSC (EM)</td><td>78.3 13.1 85.4</td><td>74.6 10.8 87.9</td><td>90.2 43.2 90.9</td><td>90.0 67.6 89.9</td><td>96.4</td><td>97.3 78.8</td></tr><tr><td></td><td>C-SimpleQA (Correct)</td><td>76.7 55.4</td><td>76.0 58.7</td><td>86.5 68.0</td><td>68.9 40.3</td><td></td><td>92.8 91.8 63.7</td></tr></table></body></html>

*表4 | DeepSeek-R1与其他代表性模型的对比*

在教育导向的知识基准测试（如MMLU、MMLU-Pro和GPQA Diamond）中，DeepSeek-R1展现出优于DeepSeek-V3的性能表现。这一提升主要归功于STEM相关题目准确率的显著提高，而这正是通过大规模强化学习实现的突破性进展。在长文本依赖型问答任务FRAMES上，DeepSeek-R1同样表现卓越，充分展现了其强大的文档分析能力，这凸显了推理模型在AI驱动的搜索与数据分析任务中的巨大潜力。事实性基准测试SimpleQA中，DeepSeek-R1超越DeepSeek-V3的表现印证了其处理事实性查询的卓越能力——这一趋势与OpenAI-ol在该基准上超越GPT-4o的现象相呼应。但值得注意的是，在中文SimpleQA基准测试中，由于安全强化学习后模型倾向于拒绝回答特定查询，DeepSeek-R1表现略逊于DeepSeek-V3。若未施加安全强化学习，DeepSeek-R1的准确率可突破70%：

DeepSeek-R1在格式指令遵循评估基准IF-Eval上同样表现优异，这一提升可归因于监督微调(SFT)和强化学习(RL)最终阶段引入的指令遵循数据。该模型在AlpacaEval2.0和ArenaHard基准上的卓越表现，印证了其在文本生成和开放域问答任务中的优势。相较于DeepSeek-V3的显著性能提升，充分证明大规模强化学习带来的泛化效益——不仅能增强推理能力，还可全面提升跨领域任务表现。值得注意的是，DeepSeek-R1生成的摘要长度保持精简，在ArenaHard上平均输出689个token，在AlpacaEval 2.0上平均生成2,218个字符。这表明该模型在基于GPT的评估中有效规避了长度偏差问题，进一步巩固了其跨任务稳健性。

在数学任务上，DeepSeek-R1展现出与OpenAI-o1-1217相当的性能，并大幅领先其他模型。这一优势同样体现在编程算法类任务中（如LiveCodeBench和Codeforces平台），专注推理的模型在这些基准测试中占据主导地位。而在工程导向的编程任务上，OpenAI-ol-1217在Aider基准优于DeepSeek-R1，但在SWE Verified基准表现相当。我们认为DeepSeek-R1的工程性能将在下一版本得到提升，因为当前相关强化学习训练数据量仍非常有限。

3.2. 蒸馏模型评估

<html><body><table><tr><td rowspan="2">Model</td><td colspan="2">AIME2024</td><td rowspan="2">MATH-500</td><td rowspan="2">GPQA Diamond</td><td rowspan="2">LiveCode Bench</td><td rowspan="2">CodeForces</td></tr><tr><td>pass@1</td><td>cons@64</td></tr><tr><td></td><td>9.3</td><td>13.4</td><td>74.6 pass@1</td><td>49.9 pass@1</td><td>32.9 pass@1</td><td>rating 759</td></tr><tr><td>GPT-40-0513 Claude-3.5-Sonnet-1022</td><td>16.0</td><td>26.7</td><td>78.3</td><td>65.0</td><td>38.9</td><td>717</td></tr><tr><td>OpenAI-o1-mini</td><td>63.6</td><td>80.0</td><td>90.0</td><td>60.0</td><td>53.8</td><td>1820</td></tr><tr><td>QwQ-32B-Preview</td><td>50.0</td><td>60.0</td><td>90.6</td><td>54.5</td><td>41.9</td><td>1316</td></tr><tr><td>DeepSeek-R1-Distill-Qwen-1.5B</td><td>28.9</td><td>52.7</td><td>83.9</td><td>33.8</td><td>16.9</td><td>954</td></tr><tr><td>DeepSeek-R1-Distill-Qwen-7B</td><td>55.5</td><td>83.3</td><td>92.8</td><td>49.1</td><td>37.6</td><td>1189</td></tr><tr><td>DeepSeek-R1-Distill-Qwen-14B</td><td>69.7</td><td>80.0</td><td>93.9</td><td>59.1</td><td>53.1</td><td>1481</td></tr><tr><td>DeepSeek-R1-Distill-Qwen-32B</td><td>72.6</td><td>83.3</td><td>94.3</td><td>62.1</td><td>57.2</td><td>1691</td></tr><tr><td>DeepSeek-R1-Distill-Llama-8B</td><td>50.4</td><td>80.0</td><td>89.1</td><td>49.0</td><td>39.6</td><td>1205</td></tr><tr><td>DeepSeek-R1-Distill-Llama-70B</td><td>70.0</td><td>86.7</td><td>94.5</td><td>65.2</td><td>57.5</td><td>1633</td></tr></table></body></html>

*表5 | DeepSeek-R1蒸馏模型与其他可比模型在推理相关基准上的对比*

如表5所示，仅通过蒸馏DeepSeek-R1的输出，就能使高效的DeepSeekR1-7B（即DeepSeek-R1-Distill-Qwen-7B，下文简称相同）全面超越GPT-4o-0513等非推理模型。DeepSeek-R1-14B在所有评估指标上均优于QwQ-32BPreview，而DeepSeek-R1-32B和DeepSeek-R1-70B在多数基准测试中显著超越ol-mini。这些结果充分证明了蒸馏方法的强大潜力。此外，我们发现对这些蒸馏模型应用强化学习能带来进一步的显著提升。鉴于该方向值得深入探索，本文仅展示简单SFT蒸馏模型的结果。

# 4. 讨论

## 4.1. 蒸馏与强化学习的对比

在3.2节中可以看到，通过蒸馏DeepSeek-R1，小模型能取得令人印象深刻的结果。但仍存在一个问题：若不经过蒸馏，仅通过本文讨论的大规模RL训练，模型能否达到可比性能？

为回答这个问题，我们在Qwen-32B-Base上使用数学、代码和STEM数据进行了超1万步的大规模RL训练，最终得到DeepSeek-R1-Zero-Qwen-32B。表6所示的实验结果表明，32B基础模型经过大规模

<html><body><table><tr><td rowspan="2">Model</td><td colspan="2">AIME 2024</td><td rowspan="2">MATH-500</td><td rowspan="2">GPQA Diamond pass@1</td><td rowspan="2">LiveCodeBench pass@1</td></tr><tr><td>pass@1</td><td>cons@64</td></tr><tr><td>QwQ-32B-Preview</td><td>50.0</td><td>60.0</td><td>90.6</td><td>54.5</td><td>41.9</td></tr><tr><td>DeepSeek-R1-Zero-Qwen-32B</td><td>47.0</td><td>60.0</td><td>91.6</td><td>55.0</td><td>40.2</td></tr><tr><td>DeepSeek-R1-Distill-Qwen-32B</td><td>72.6</td><td>83.3</td><td>94.3</td><td>62.1</td><td>57.2</td></tr></table></body></html>

*表6 | 推理相关基准测试中蒸馏模型与强化学习模型的对比*

RL训练后，其性能与QwQ-32B-Preview相当。然而从DeepSeek-R1蒸馏得到的DeepSeek-R1-Distill-Qwen-32B，在所有基准测试中都显著优于DeepSeek-R1-Zero-Qwen-32B。

由此我们可以得出两个结论：首先，将更强大的模型蒸馏至小模型能产生优异效果，而依赖本文所述大规模RL的小模型不仅需要巨大算力支撑，其性能甚至可能无法达到蒸馏效果；其次，尽管蒸馏策略兼具经济性与有效性，但想要突破智能边界仍需更强大的基础模型和更大规模的强化学习。

## 4.2. 失败的尝试

在开发DeepSeek-R1的早期阶段，我们也曾遭遇过失败与挫折。在此分享失败经验以提供启示，但这并不意味着这些方法无法开发出有效的推理模型。

过程奖励模型（PRM）PRM是引导模型寻找更优推理任务解决方法的合理方案。然而实践中，PRM存在三个主要局限可能阻碍其最终成功：首先，在通用推理中明确定义细粒度步骤具有挑战性；其次，判断当前中间步骤正确与否是项艰巨任务——基于模型的自动标注效果欠佳，而人工标注不利于规模化扩展；第三，一旦引入基于模型的PRM，必然导致奖励破解现象，且重新训练奖励模型需额外资源并会使整个训练流程复杂化。综上，虽然PRM在重排模型生成的Top-N响应或辅助引导搜索方面表现良好，但在我们实验的大规模强化学习过程中，其优势相较于引入的额外计算开销而言较为有限。

蒙特卡洛树搜索（MCTS）受AlphaGo和AlphaZero的启发，我们探索了利用蒙特卡洛树搜索（MCTS）来增强测试时计算可扩展性。该方法通过将答案分解为更小的部分，使模型能够系统性地探索解空间。为实现这一目标，我们引导模型生成与搜索所需特定推理步骤相对应的多个标签。在训练阶段，首先使用预训练的价值模型引导MCTS，通过收集的提示词来寻找答案；随后利用生成的问题-答案对同时训练执行模型和价值模型，并迭代优化整个过程。

然而，该方法在扩大训练规模时面临若干挑战。首先，与国际象棋相对明确的搜索空间不同，令牌生成呈现指数级更大的搜索空间。为此我们为每个节点设置了最大扩展限制，但这可能导致模型陷入局部最优。其次，价值模型直接影响生成质量，因为它指导着搜索过程的每一步。训练细粒度价值模型本身具有较高难度，这使得模型难以实现迭代改进。虽然AlphaGo的核心成功依赖于通过训练价值模型逐步提升性能，但由于令牌生成的复杂性，这一原理在我们的实验设置中难以复现。

总之，尽管蒙特卡洛树搜索（MCTS）配合预训练价值模型能在推理阶段提升性能，但通过自我搜索实现模型性能的迭代提升仍是一个重大挑战。

# 5. 结论、局限性与未来工作

本研究中，我们分享了通过强化学习提升模型推理能力的探索历程。DeepSeek-R1-Zero采用不依赖冷启动数据的纯强化学习方法，在多项任务中展现出强劲性能。而更强大的DeepSeek-R1则结合冷启动数据与迭代式强化学习微调，最终在一系列任务上达到与OpenAI-o1-1217相当的水平。

我们进一步探索了向小型稠密模型蒸馏推理能力的方法。以DeepSeek-R1作为教师模型生成80oK训练样本，并对多个小型稠密模型进行微调。结果令人振奋：DeepSeek-R1-Distill-Qwen-1.5B在数学基准测试中超越GPT-4o和Claude-3.5-Sonnet，AIME得分达28.9%，MATH得分达83.9%。其他稠密模型同样取得显著成果，其性能远超基于相同基础检查点的其他指令调优模型。

未来，我们计划针对DeepSeek-R1在以下研究方向展开深入探索：

· 通用能力：当前DeepSeek-R1在函数调用、多轮对话、复杂角色扮演和JSON输出等任务上的表现仍落后于DeepSeek-V3。我们将研究如何利用长链思维推理（CoT）来提升这些领域的任务表现。

· 语言混合问题：当前DeepSeek-R1主要针对中英文优化，在处理其他语言查询时可能出现语言混杂现象。例如即使用户使用非中英文提问，模型仍可能采用英文进行推理和回复。我们将在后续版本中解决这一局限性。

· 提示工程：评估发现DeepSeek-R1对提示词较为敏感，少量示例提示（few-shot）往往会降低其表现。因此建议用户采用零样本（zero-shot）设置，直接描述问题并明确指定输出格式以获得最佳效果。

· 软件工程任务：由于评估耗时较长会影响强化学习效率，目前大规模强化学习尚未广泛应用于软件工程任务。这导致DeepSeek-R1在软件工程基准测试上相较DeepSeek-V3提升有限。未来版本将通过软件工程数据的拒绝采样（rejection sampling）或在强化学习过程中引入异步评估机制来提升效率。

# 参考文献

AI@Meta. Llama 3.1 model card, 2024. URL https: //github.com/meta-llama/llama-m odels/blob/main/models/llama3_1/MODEL_CARD.md.

Anthropic. Claude 3.5 sonnet, 2024. URL https ://www.anthropic.com/news/claude-3 -5-sonnet.

M. Chen, J. Tworek, H. Jun, Q. Yuan, H. P.de Oliveira Pinto, J. Kaplan, H. Edwards, Y. Burda, N. Joseph, G. Brockman, A. Ray, R. Puri, G. Krueger, M.Petrov, H. Khlaaf, G.Sastry, P. Mishkin, B. Chan, S. Gray, N. Ryder, M. Pavlov, A. Power, L. Kaiser, M. Bavarian, C. Winter, P. Tillet, F. P. Such, D. Cummings, M. Plappert, F. Chantzis, E. Barnes, A. Herbert-Voss, W. H. Guss, A. Nichol, A. Paino, N. Tezak, J. Tang, I. Babuschkin, S.Balaji, S. Jain, W.Saunders, C. Hesse, A. N. Carr, J. Leike, J. Achiam, V. Misra, E.Morikawa, A. Radford, M. Knight, M. Brundage, M. Murati, K. Mayer, P. Welinder, B. McGrew, D. Amodei, S. McCandlish, I. Sutskever, and W. Zaremba. Evaluating large language models trained on code. CoRR, abs/2107.03374, 2021. URL https://arxiv.org/abs/2107.03374.

A. Dubey, A. Jauhri, A. Pandey, A. Kadian, A. Al-Dahle, A. Letman, A. Mathur, A. Schelten, A. Yang, A. Fan, et al. The lama 3 herd of models. arXiv preprint arXiv:2407.21783, 2024.

Y. Dubois, B. Galambosi, P. Liang, and T. B. Hashimoto. Length-controlld alpacaeval: A simple way to debias automatic evaluators. arXiv preprint arXiv:2404.04475, 2024.

X. Feng, Z. Wan, M. Wen, S. M. McAleer, Y. Wen, W. Zhang, and J. Wang. Alphazero-like tree-search can guide large language model decoding and training, 2024. URL https : //arxiv.org/abs/2309.17179.

L. Gao, J. Schulman, and J. Hilton. Scaling laws for reward model overoptimization, 2022. URL https://arxiv.org/abs/2210.10760.

A. P. Gema, J. O. J. Leang, G. Hong, A. Devoto, A. C. M. Mancino, R. Saxena, X. He, Y. Zhao, X. Du, M. R. G. Madani, C. Barale, R. McHardy, J. Harris, J. Kaddour, E. van Krieken, and P. Minervini. Are we done with mmlu? CoRR, abs/2406.04127, 2024. URL https : //doi .or g/10.48550/arXiv.2406.04127.

Google. Our next-generation model: Gemini 1.5, 2024. URL https : //blog.google/techno logy/ai/google-gemini-next-generation-model-february-2024.

Y. He, S.Li, J.Liu, Y.Tan, W. Wang, H.Huang, X.Bu, H.Guo, C.Hu, B. Zheng, et al. Chinese simpleqa: A chinese factuality evaluation for large language models. arXiv preprint arXiv:2411.07140, 2024.

D. Hendrycks, C. Burns, S. Basart, A. Zou, M.Mazeika, D.Song, and J. Steinhardt. Measuring massive multitask language understanding. arXiv preprint arXiv:2009.03300, 2020.

Y. Huang, Y. Bai, Z. Zhu,J. Zhang,J. Zhang, T.Su, J. Liu, C. Lv, Y. Zhang, J. Lei, et al.C-Eval: A multi-level multi-discipline chinese evaluation suite for foundation models. arXiv preprint arXiv:2305.08322, 2023.

N. Jain, K.Han, A.Gu, W. Li, F. Yan, T. Zhang, S. Wang, A.Solar-Lezama, K.Sen, and I. Stoica. Livecodebench: Holistic and contamination free evaluation of large language models for code. CoRR, abs/2403.07974, 2024. URL https://doi.org/10.48550/arXiv.2403.07974.

S. Krishna, K. Krishna, A. Mohananey, S. Schwarcz, A. Stambler, S. Upadhyay, and M. Faruqui. Fact, fetch, and reason: A unified evaluation of retrieval-augmented generation. CoRR, abs/2409.12941, 2024. doi: 10.48550/ARXIV.2409.12941. URL https : //doi .org/10.485 50/arXiv.2409.12941.

A. Kumar, V. Zhuang, R. Agarwal, Y. Su, J. D. Co-Reyes, A. Singh, K. Baumli, S. Iqbal, C. Bishop, R. Roelofs, et al. Training language models to self-correct via reinforcement learning. arXiv preprint arXiv:2409.12917, 2024.

H. Li, Y. Zhang, F. Koto, Y. Yang, H. Zhao, Y. Gong, N. Duan, and T. Baldwin. CMMLU: Measuring massive multitask language understanding in Chinese. arXiv preprint arXiv:2306.09212, 2023.

T. Li, W.-L. Chiang, E. Frick, L. Dunlap, T. Wu, B. Zhu, J. E. Gonzalez, and I. Stoica. From crowdsourced data to high-quality benchmarks: Arena-hard and benchbuilder pipeline. arXiv preprint arXiv:2406.11939, 2024.

H. Lightman, V. Kosaraju, Y. Burda, H. Edwards, B. Baker, T. Lee, J. Leike, J. Schulman, I. Sutskever, and K.Cobbe. Let's verify step by step. arXiv preprint arXiv:2305.20050, 2023.

B. Y. Lin. ZeroEval: A Unified Framework for Evaluating Language Models, July 2024. URL https://github.com/WildEval/ZeroEval.

MAA. American invitational mathematics examination - aime. In American Invitational Mathematics Examination - AIME 2024, February 2024. URL https ://maa.org/math -competitions/american-invitational-mathematics-examination-aime.

OpenAI. Hello GPT-4o, 2024a. URL https : //openai .com/index/hello-gpt-40/.

OpenAI. Learning to reason with llms, 2024b. URL https: //openai .com/index/learnin g-to-reason-with-llms/.

OpenAI. Introducing SimpleQA, 2024c. URL https : //openai.com/index/introducing -simpleqa/.

OpenAI. Introducing SWE-bench verified we're releasing a human-validated subset of swebench that more, 2024d. URL https://openai.com/index/introducing-swe-bench -verified/.

Qwen. Qwq: Reflect deeply on the boundaries of the unknown, 2024a. URL https: //qwenlm .github.io/blog/qwq-32b-preview/.

Qwen. Qwen2.5: A party of foundation models, 2024b. URL https : //qwenlm.github.io/b log/qwen2.5.

D. Rein, B. L.Hou, A. C. Stickland, J. Petty, R. Y. Pang, J. Dirani, J. Michael, and S. R.Bowman. GPQA: A graduate-level google-proof q&a benchmark. arXiv preprint arXiv:2311.12022, 2023.

Z. Shao, P. Wang, Q. Zhu, R. Xu, J. Song, M. Zhang, Y. Li, Y. Wu, and D. Guo. Deepseekmath: Pushing the limits of mathematical reasoning in open language models. arXiv preprint arXiv:2402.03300, 2024.

D. Silver, T.Hubert, J. Schrittwieser, I. Antonoglou, M. Lai, A. Guez, M. Lanctot, L. Sifre, D. Kumaran, T. Graepel, T. P. Lillicrap, K. Simonyan, and D. Hassabis. Mastering chess and shogi by self-play with a general reinforcement learning algorithm. CoRR, abs/1712.01815, 2017a. URLhttp://arxiv.org/abs/1712.01815.

D. Silver, J. Schrittwieser, K. Simonyan, I. Antonoglou, A. Huang, A. Guez, T. Hubert, L. Baker, M. Lai, A. Bolton, Y. Chen, T. P. Lilicrap, F. Hui, L. Sifre, G. van den Driessche, T. Graepel, and D. Hassabis. Mastering the game of go without human knowledge. Nat., 550(7676):354-359, 2017b. doi: 10.1038/NATURE24270. URL https://doi.org/10.1038/nature24270.

C. Snell, J. Lee, K. Xu, and A. Kumar. Scaling llm test-time compute optimally can be more effective than scaling model parameters, 2024. URL https://arxiv .org/abs/2408.033 14.

T. Trinh, Y. Wu, Q. Le, H. He, and T. Luong. Solving olympiad geometry without human demonstrations. Nature, 2024. doi: 10.1038/s41586-023-06747-5.

J. Uesato, N. Kushman, R. Kumar, F. Song, N. Siegel, L. Wang, A. Creswell, G. Irving, and I. Higgins. Solving math word problems with process-and outcome-based feedback. arXiv preprint arXiv:2211.14275, 2022.

P. Wang, L.Li, Z.Shao, R. Xu, D. Dai, Y. Li, D. Chen, Y. Wu, and Z.Sui. Math-shepherd: A labelfree step-by-step verifier for llms in mathematical reasoning. arXiv preprint arXiv:2312.08935, 2023.

X. Wang, J. Wei, D. Schuurmans, Q. Le, E. Chi, S. Narang, A. Chowdhery, and D. Zhou. Self-consistency improves chain of thought reasoning in language models. arXiv preprint arXiv:2203.11171, 2022.

Y. Wang, X. Ma, G. Zhang, Y. Ni, A. Chandra, S. Guo, W. Ren, A. Arulraj, X. He, Z. Jiang, T. Li, M. Ku, K. Wang, A. Zhuang, R. Fan, X. Yue, and W. Chen. Mmlu-pro: A more robust and challenging multi-task language understanding benchmark. CoRR, abs/2406.01574, 2024. URL https://doi.org/10.48550/arXiv.2406.01574.

C. S. Xia, Y. Deng, S. Dunn, and L. Zhang. Agentless: Demystifying llm-based sofware engineering agents. arXiv preprint, 2024.

H. Xin, Z. Z. Ren, J. Song, Z.Shao, W. Zhao, H. Wang, B. Liu, L. Zhang, X. Lu, Q. Du, W. Gao, Q. Zhu, D. Yang, Z. Gou, Z. F. Wu, F. Luo, and C. Ruan. Deepseek-prover-v1.5: Harnessing proof assistant feedback for reinforcement learning and monte-carlo tree search, 2024. URL https://arxiv.org/abs/2408.08152.

J. Zhou, T. Lu, S.Mishra, S.Brahma, S. Basu, Y. Luan, D. Zhou, and L.Hou. Instruction-following evaluation for large language models. arXiv preprint arXiv:2311.07911, 2023.

