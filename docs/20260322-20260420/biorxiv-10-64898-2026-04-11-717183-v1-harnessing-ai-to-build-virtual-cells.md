---
title: Harnessing AI to Build Virtual Cells
title_zh: 利用人工智能构建虚拟细胞
authors: "Cheng, X., Li, P., Guo, H., Liang, Y., Gong, J., de Vazelhes, W., Gou, C., Xie, P., Song, L., Xing, E. P."
date: 2026-04-14
pdf: "https://www.biorxiv.org/content/10.64898/2026.04.11.717183v1.full.pdf"
tags: ["query:virtcell"]
score: 10.0
evidence: 用于虚拟细胞和扰动响应模型的AI系统
tldr: 本文提出VCHarness，一个结合AI编码代理与多模态生物基础模型的自主系统，用于自动构建细胞扰动—响应模型。该系统能够探索模型架构与训练方案，显著减少人工干预时间，在多个任务上超过专家设计模型，展现AI在构建“虚拟细胞”——细胞多尺度世界模型方面的潜力。
source: biorxiv
selection_source: fresh_fetch
figures_json: "[{\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-04-11-717183-v1/fig-001.webp\", \"caption\": \"Fig. 3. VCHarness discovers non-obvious architectural patterns through search. a, MCTS visualization for the hTERT-RPE1 DEG-classification campaign. Node color encodes validation macro-F1, and the highlighted trajectory shows how search progressively concentrates on higher-performing regions of program space. b, Representative local edits made along the successful branch in a. These ranked modifications illustrate how performance gains arise from sequential architecture and optimization changes rather than from a single one-step jump. c, Architecture recovered at the node marked ⑨ in a. The discovered model combines graph structure, selective fine-tuning, and perturbation-conditioned computation, illustrating how VCHarness assembles executable programs that differ from simpler modality-isolated baselines. d, Correlation between validation and test scores across evaluated nodes. The near-linear agreement indicates that validation-guided selection generalizes reliably to held-out test data. e, Aggregate motif analysis over searched architectures. By grouping discovered models according to frequently occurring design choices, this panel highlights neural-architecture motifs that are repeatedly associated with stronger performance.\", \"page\": 6, \"index\": 1, \"width\": 925, \"height\": 817}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-04-11-717183-v1/fig-002.webp\", \"caption\": \"Fig. 9. MPRA WTC11 architecture and search summary. a, MCTS search tree for MPRA wtc11 fine-tuning (125 nodes, 2 seeds). Node color encodes validation Pearson r (0.071–0.849). b, Architecture of the bestperforming node (node1-3-2-1-2, val r = 0.849). c, Winning improvement path, selected by validation score. d, Training curves for the best node (node1-3-2-1-2, selected by validation score). e, Validation vs test Pearson r for all nodes in the search tree. Pearson r = 0.975. f, Feature analysis across all nodes. Dual-axis bar charts show node count and mean test Pearson r ± std.\", \"page\": 21, \"index\": 2, \"width\": 608, \"height\": 1121}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-04-11-717183-v1/fig-003.webp\", \"caption\": \"Fig. 6. Architecture discovery on K562. a, MCTS visualization for the K562 Essential campaign. b, Ranked local modifications along a successful branch. c, Best-discovered K562 model architecture. d, Correlation between validation and test scores across evaluated nodes. e, Aggregate motif analysis over searched architectures, summarizing recurring architectural patterns associated with improved K562 performance. In K562, successful nodes repeatedly combined strong cell-level backbones with graph-based perturbation modules and gated fusion, suggesting a particularly stable interaction between pretrained cellular representations and explicit network priors.\", \"page\": 18, \"index\": 3, \"width\": 925, \"height\": 846}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-04-11-717183-v1/fig-004.webp\", \"caption\": \"Fig. 7. MPRA K562 architecture and search summary. a, MCTS search tree for MPRA-K562 fine-tuning (37 nodes, 2 seeds). Node color encodes validation Pearson r (0.694–0.876). Seed 1: AlphaGenome pretrained encoder; Seed 2: CNN from scratch. b, Architecture of the best-performing node (node1-3-3-1, val r = 0.876): AlphaGenome CNN encoder with flatten concatenation and 2-layer MLP head, trained with two-stage strategy (frozen encoder then full fine-tuning). c, Winning improvement path. Each row shows one MCTS iteration along the best branch, selected by validation score. d, Training curves for the best node (node1-3-3-1, selected by validation score). Top: validation Pearson r across Stage 1 (head-only training) and Stage 2 (full encoder finetuning). Bottom: training loss. e, Validation vs test Pearson r for all nodes in the search tree. Pearson r = 0.999 between validation and test scores. f, Feature analysis across all nodes. Dual-axis bar charts show node count (blue) and mean test Pearson r ± std (green) for each category of pretrained model, fine-tuning strategy, head type, and learning rate scheduler.\", \"page\": 19, \"index\": 4, \"width\": 943, \"height\": 1116}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-04-11-717183-v1/fig-005.webp\", \"caption\": \"Fig. 5. Architecture discovery on Jurkat. a, MCTS visualization for the Jurkat Essential campaign. b, Ranked local modifications along a successful branch. c, Best-discovered Jurkat model architecture. d, Correlation between validation and test scores across evaluated nodes. e, Aggregate motif analysis over searched architectures, highlighting recurrent neural-architecture motifs associated with stronger Jurkat performance. Relative to HepG2, the stronger Jurkat nodes more often relied on compact architectures with explicit perturbation modeling and lighter fusion strategies.\", \"page\": 17, \"index\": 5, \"width\": 921, \"height\": 822}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-04-11-717183-v1/fig-006.webp\", \"caption\": \"Fig. 8. MPRA HepG2 architecture and search summary. a, MCTS search tree for MPRA HepG2 fine-tuning (55 nodes, 2 seeds). Node color encodes validation Pearson r (-0.028–0.888). Seed 1: AlphaGenome pretrained encoder; Seed 2: CNN from scratch. b, Architecture of the best-performing node (node1-3-2, val r = 0.9998). c, Winning improvement path, selected by validation score. d, Training curves for the best node (node1-3-2, selected by validation score). e, Validation vs test Pearson r for all nodes in the search tree. Pearson r = 0.9998. f, Feature analysis across all nodes. Dual-axis bar charts show node count and mean test Pearson r ± std.\", \"page\": 20, \"index\": 6, \"width\": 809, \"height\": 1026}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-04-11-717183-v1/fig-007.webp\", \"caption\": \"Fig. 2. VCHarness performance and search dynamics across CRISPR perturbation settings. a, VCHarness (blue) outperforms human-designed models grouped by input modality or knowledge source across four differentially expressed gene (DEG) classification tasks on four cell lines (HepG2, K562, Jurkat, and hTERT-RPE1); dashed lines indicate mean performance. Baselines are from the foundation-models-perturbation repository (https://github.com/genbio-ai/foundation-models-perturbation/tree/main/results/ scores). Consistent gains across cell lines demonstrate transferability of the autonomous search loop across cell lines. The y-axis corresponds to test macro-F1 scores. b, Best-so-far trajectories during Monte Carlo tree search (MCTS). Grey dots denote evaluated candidates, and blue lines indicate the running best. Rapid early improvement followed by gradual refinement reflects efficient allocation of search effort. The x-axis represents candidate implementations ordered by evaluation time, and the y-axis denotes validation macro-F1 scores.\", \"page\": 5, \"index\": 7, \"width\": 941, \"height\": 860}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-04-11-717183-v1/fig-008.webp\", \"caption\": \"Fig. 4. Architecture discovery on HepG2. a, MCTS visualization for the HepG2 Essential campaign. b, Ranked local modifications along a successful branch, showing how search improves performance through sequential edits. c, Best-discovered model architecture recovered from the highlighted branch. d, Correlation between validation and test scores across evaluated nodes, supporting the use of validation performance as a practical search objective. e, Aggregate motif analysis over searched architectures, summarizing which neural-architecture choices recur most often among stronger HepG2 models. In this campaign, the best-performing solutions repeatedly favored multimodal fusion centered on graph-based perturbation structure with additional pretrained expression features.\", \"page\": 16, \"index\": 8, \"width\": 921, \"height\": 762}]"
motivation: 当前细胞过程建模依赖专家手动设计与调试，效率低且难以扩展，需要更自动化的方案。
method: 通过AI编码代理与多模态生物模型结合，自动生成、评估和优化扰动响应模型架构。
result: VCHarness在多个基因扰动响应基准上优于专家设计的模型，并将模型开发周期由数月缩短至数天。
conclusion: 该研究证明了自动化AI系统可替代人工进行模型构建，推动虚拟细胞研究的可扩展与数据驱动发展。
---

## 摘要
虚拟细胞是细胞的世界模型：一种能够跨不同模态与尺度预测、模拟和编程细胞过程的计算系统。实现这一目标的重要途径是对遗传和化学扰动如何引发转录响应进行建模，这一能力是理解疾病机制与药物研发的核心。然而，当前方法仍需大量专家参与，依赖于长达数月的反复手动模型设计、训练与调试。

在此，我们提出 VCHarness，一种自主构建扰动-响应模型的人工智能系统，它结合了 AI 编码代理与多模态生物基础模型。该系统以最少的人为干预探索庞大的架构与训练流程空间，迭代生成、评估并优化候选模型。在多个扰动-响应基准测试中，VCHarness 识别出的架构表现优于专家设计的方法，同时将开发周期从数月缩短至数日。此外，它还发现了一些与性能提升相关的非显而易见的架构模式，表明自动化搜索能够突破传统设计策略。这些结果提示，从人工设计模型向用于构建虚拟细胞世界模型组件的自主系统转变，正使对细胞系统的可扩展、数据驱动探索成为可能。

## Abstract
A virtual cell is a world model of a cell: a computational system that predicts, simulates and programs cellular processes across modalities and scales. An important path toward this goal is to model how genetic and chemical perturbations give rise to transcriptional responses, a core capability for disease understanding and drug discovery. However, current approaches remain expert-intensive, relying on iterative manual model design, training and debugging over months.

Here we present VCHarness, an autonomous AI system that constructs perturbation-response models by combining an AI coding agent with multimodal biological foundation models. The system explores large spaces of architectures and training pipelines with minimal human intervention, iteratively generating, evaluating and refining candidate models. Across multiple perturbation-response benchmarks, VCHarness identifies architectures that outperform expert-designed approaches while reducing development time from months to days. It further uncovers non-obvious architectural patterns associated with improved performance, indicating that automated search can extend beyond conventional design strategies. These results suggest a shift from manually engineered models toward autonomous systems for constructing components of virtual cell world models, enabling scalable and data-driven exploration of cellular systems.

---

## 论文详细总结（自动生成）

# 《Harnessing AI to Build Virtual Cells》论文总结

## 1. 核心问题与研究动机

- **研究背景**：  
  虚拟细胞（Virtual Cell）旨在建立一个多尺度、多模态的细胞世界模型，用以预测、模拟并编程细胞的动态行为。其核心能力之一是预测基因或化学扰动下的转录响应，这对于疾病机制研究与药物发现至关重要。  
- **现有问题**：  
  现有扰动—响应建模仍高度依赖人工专家的经验，需手动设计模型、调参与调试，周期长达数月；模型性能受设计选项影响大，人工探索困难且效率低。  
- **研究目标**：  
  作者希望通过自动化系统取代人工模型构建流程，实现从数据输入到模型生成、训练与评价的全自动闭环，显著提升效率与可扩展性，从而推动虚拟细胞的可计算实现。

---

## 2. 方法论：VCHarness 系统原理与核心结构

### 2.1 总体思路

- **VCHarness 定义**：一种自主构建细胞扰动—响应模型的 AI 系统，可在最小人工干预下自动探索模型架构与训练流程。
- **核心思想**：  
  将整个模型开发过程（代码生成、调试、执行、评估、优化）视作一个可搜索的程序空间问题，以自动探索和优化完整的训练管线。

### 2.2 关键组成模块

- **生物基础模型组件 (Biological Foundation Models)**：  
  使用多模态预训练模型作为可复用的表征原语，如：
  - **AIDO.DNA**, **AIDO.Protein**, **AIDO.Cell**, **AIDO.DNA2**；
  - 公共模型如 **ESM2**, **Geneformer**, **scGPT**, **scFoundation**, **STRING-GNN** 等。
  
- **AI 编码代理 (Coding Agent)**：  
  - 由大型语言模型（Claude Sonnet 4.6）驱动；
  - 具备约 100 种专业技能（数据处理、模型融合、分布式训练、结果汇总、调试修复等）；
  - 执行任务包括代码生成、错误修复、结果总结、记忆写入和循环优化。

- **蒙特卡洛树搜索 (Monte Carlo Tree Search, MCTS)**：  
  - 控制探索与利用的平衡，以节点作为候选程序；
  - 每个节点代表一个完整的可运行训练管线；
  - 使用上置信界（UCB）作为节点选择准则：  
    \[
    UCB(i) = \bar{J_i} + c \sqrt{\frac{\log N}{n_i}}
    \]
    其中 \( \bar{J_i} \) 为节点平均得分，\(n_i\) 为节点访问次数，\(N\) 为父节点访问次数，\(c\) 为平衡系数。

- **反馈与记忆机制**：  
  每次迭代后，系统记录训练输出、验证指标、错误日志和执行成本，并将这些经验写入全局记忆，用于指导后续程序生成。

- **分布式执行引擎**：  
  候选程序在 GPU 集群上并行执行，各节点异步运行，中心化同步搜索树状态，容错且支持自我恢复。

### 2.3 工作流程（闭环）

1. 给定任务与数据集描述；  
2. Coding Agent 生成初始候选程序；  
3. 自动调试与执行模型训练；  
4. 收集评估指标（如 Macro-F1、Pearson 相关系数等）；  
5. 将反馈写入记忆并更新 MCTS 树；  
6. 根据历史经验生成新的候选代码。  
→ 重复直至计算预算或性能收敛。

---

## 3. 实验设计

### 3.1 应用任务与数据集

- **主要任务**：基因扰动—响应预测（即CRISPR扰动对应差异表达基因分类任务）。
- **数据来源**：
  - 来自汇总的 **Essential** 数据集、CRISPR-Perturb-seq 等；
  - 涵盖四个不同细胞系：**HepG2、K562、Jurkat、hTERT-RPE1**；
  - 另在附录扩展至 **MPRA（massively parallel reporter assay）** 表达预测实验，数据来自三种细胞：**K562、HepG2、WTC-11**。
  
### 3.2 对比基线

包括多种专家设计模型或预训练架构：
- **Foundation 模型类**：Geneformer、scGPT、AIDO.Cell。
- **图神经网络类**：STRING GNN、TranscriptFormer。
- **无预训练对照**：随机嵌入、简单多层感知机（MLP）、常数预测等。

### 3.3 评估指标

- CRISPR DEGs 任务采用 Macro-F1；
- MPRA 表达预测任务采用 Pearson 相关系数；
- 同时追踪验证—测试得分相关性（用于评估泛化一致性）。

---

## 4. 算力与运行资源

- **系统计算要素**：
  - GPU：NVIDIA H100；
  - 使用 Kubernetes 与 Ray 分布式执行；
  - 每个节点平均运行时间约 **60 分钟**，其中：
    - 模型训练占 **59% 的运行时间**；
    - 平均每节点花费约 **\$6–7 美元**；
  - VCHarness 支持多 worker 并行分布执行。  
- **训练总体规模**：未明确披露 GPU 数量或总运行时长，但实验在多数据集、多任务 parallel setting 下完成，说明算力充足。

---

## 5. 实验规模与充分性

- **主要实验数量**：
  - 四个 CRISPR 细胞系 × 多轮搜索，共 1300+ MCTS 节点评估；
  - 附录包含三个 MPRA 任务（共超过 200 个节点搜索轨迹）；
  - 每个任务均给出多分支搜索可视化、架构差异分析与消融说明。
- **实验充分性**：
  - 对比全面、包括跨任务、跨模态与消融；
  - 验证—测试指标线性相关性高（>0.97），表明结果稳定；
  - 结果具有跨细胞类型可迁移性；
  - 整体实验设置客观、公平且配对基线明确。

---

## 6. 主要结论与发现

- **性能结果**：
  - 在所有四个扰动-response任务上，VCHarness 均超越专家设计模型；
  - 平均 Macro-F1 提升约 0.04（从 ~0.44 提升至 ~0.48–0.51）；
  - MPRA 任务上 Pearson r 提升达 +0.05 至 +0.07；
  - 模型开发周期从数月缩短至数日。
  
- **发现**：
  - 自动搜索能发掘 **非显而易见的架构模式**，如：
    - STRING-GNN 模块与细胞表达预训练模型的 gated-fusion；
    - 局部 fine-tuning 优于全量微调；
    - LoRA 等参数高效化策略反复被发现。
  - 支持“经验自动化”：系统自动发现可迁移的通用神经结构 motifs。
  - 验证—测试一致性高，表明搜索过程无显著过拟合。

---

## 7. 优点与创新亮点

- **方法创新**：
  - 将模型建设问题表述为“可执行程序搜索”；
  - 构建闭环 AI-on-AI 系统，融合 LLM 编码、搜索、调试与反馈。
- **系统化设计**：
  - 集成 100+ 生物任务技能、自动分布式运行框架；
  - 可跨任务迁移的搜索策略。
- **效率提升**：
  - 显著缩短模型开发时间；
  - 自动发现跨细胞通用架构模式；
  - 成本控制良好（主要集中在模型执行阶段）。
- **实验标准化**：
  - 支持多领域复现与自动报告生成；
  - 性能一致性验证充分。

---

## 8. 不足与局限

- **迁移与复用受限**：  
  历史记忆尚不能充分跨任务复用，经验迁移尚依赖手动检查。
- **生物学解释性不足**：  
  自动搜索得到的架构尽管准确，但缺乏直接生物学可解释性；需引入机制约束或生物学先验。
- **搜索效率与成本**：  
  评估过程仍受限于训练成本；未来可结合多保真度评估或早停策略。
- **应用范围限制**：  
  当前任务集中于转录组扰动与 MPRA，尚未涵盖细胞时间动态、多模态与细胞–细胞交互。

---

**（完）**
