---
title: Rapid and Reliable Structural Modeling of Adaptive Immune Receptors Using an Optimized AlphaFold3 workflow
title_zh: 利用优化的AlphaFold3工作流程对适应性免疫受体进行快速且可靠的结构建模
authors: "Jann, A., Perez, M. A. S., Zoete, V."
date: 2026-04-15
pdf: "https://www.biorxiv.org/content/10.64898/2025.12.19.695451v2.full.pdf"
tags: ["query:gentcr"]
score: 9.5
evidence: 利用深度学习进行 T 细胞受体结构建模
tldr: 本研究针对AlphaFold3在适应性免疫受体结构预测中的应用进行优化，通过调整MSA组成和推理阶段数量，利用精简的UniRef90子集构建了一个快速高效的建模流程，可在保持准确性的前提下实现约45倍的加速，为大规模免疫学研究提供高通量结构预测方案。
source: biorxiv
selection_source: fresh_fetch
figures_json: "[{\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2025-12-19-695451-v2/fig-001.webp\", \"caption\": \"Figure 1. a) General overview of AF3 original workflow and our AF3 variant workflow, along with running 74 time of the corresponding AF3 MSA and inference phases. The original AF3 uses 4 databases to build the 75 MSA input while AF3 variant uses a much smaller database named UniRef90-TCR or UniRef90-Ab. b) 76 Process used to build the reduced Uniref90-TCR/Ab databases, by sequentially generating MSAs for 77 individual TCRs using JackHMMER and the UniRef90 database, and aggregating the resulting sequences. 78\", \"page\": 4, \"index\": 1, \"width\": 990, \"height\": 825}]"
motivation: AlphaFold在抗体和T细胞受体建模中的潜力巨大，但当前模型在计算效率和预测针对性上仍需优化。
method: 作者系统评估了AlphaFold3的MSA组成和推理阶段数，设计出针对抗体与TCR结构建模的高速高准优化流程。
result: 改进后的AlphaFold3工作流程在保持高准确性的同时，实现了约45倍的速度提升。
conclusion: 该优化工作流程为快速、可靠的免疫受体结构建模奠定基础，有助于加速治疗发现和免疫识别机制研究。
---

## 摘要
AlphaFold（AF）是一种基于深度学习的蛋白质建模方法，它通过在蛋白质结构预测中普遍达到近乎实验精度，革新了结构生物学。AF的一个重要应用是抗体（Abs）和T细胞受体（TCRs）的建模，这些作为细胞免疫的关键介质，其结构特异性决定了在癌症、感染和自身免疫疾病中的反应。在本研究中，我们系统分析了AF3的性能，考察了MSA组成和推理阶段数量对预测准确性与计算效率的影响。利用精简后的UniRef90子集，我们提出了一种约快45倍、且高度准确的AF3流程变体，专门用于优化抗体和TCR受体结构域的建模，从而实现快速、可靠的结构预测，适用于高通量免疫学研究的规模。我们的发现为更快速的治疗性发现和更深入的免疫识别分子机制理解奠定了基础。

## Abstract
AlphaFold (AF), a deep-learning based protein modelling approach, has revolutionized structural biology by generally achieving near-experimental accuracy in protein structure prediction. An impactful application of AF is the modelling of antibodies (Abs) and T-cell receptors (TCRs), key mediators of cellular immunity, whose structural specificity underlies responses in cancer, infection, and autoimmune diseases. In this work, we analyse AF3 performance by systematically examining how MSA composition and the number of inference phases affect prediction accuracy and computational efficiency. Using reduced UniRef90 subsets, we present a ~45-fold accelerated and highly accurate variant of the AF3 workflow specifically optimized for the modelling of the Abs and TCRs receptor domains, enabling rapid, reliable structural predictions at a scale suitable for high-throughput immunological studies. Our findings provide a foundation for faster therapeutic discovery and deeper molecular mechanism understanding of immune recognition.

---

## 论文详细总结（自动生成）

# 利用优化的 AlphaFold3 工作流程对适应性免疫受体进行快速且可靠的结构建模 — 中文总结

---

## 一、研究动机与背景

- **核心问题**：AlphaFold 的传统结构预测流程计算量巨大，尤其在多序列比对（MSA）阶段。对于抗体（Abs）和 T 细胞受体（TCRs）这类具有高度可变性和结构复杂度的免疫受体，大规模结构建模的计算瓶颈十分突出。  
- **研究目标**：作者希望在不显著降低预测准确度的前提下，优化 AlphaFold3（AF3）的计算效率，使其适应高通量免疫学研究。  
- **背景意义**：抗体和 TCRs 的三维结构是揭示免疫识别机制和指导癌症免疫治疗的重要基础，但现有 AF3 模型的 MSA 阶段耗时超过总执行时间的 90%，严重制约了应用规模化。

---

## 二、方法论与技术路线

### 1. 核心思想
通过**精简 MSA 数据库**和**优化 AF3 推理参数**，在保持近实验分辨率的预测精度下，显著提升运行速度。

### 2. 技术细节
- **MSA 阶段优化**：
  - 使用 *JackHMMER* 从 UniRef90 数据库中逐步生成并聚合 TCR 与抗体的相关序列。
  - 构建新的精简数据库：**UniRef-TCR**（261,780 序列）、**UniRef-Ab**（250,160 序列）与**UniRef-textmining**（41,055 序列）。
  - 仅保留约 <3% 的原始 UniRef90 序列即可重现完整 MSA 效果。
- **推理阶段优化**：
  - 修改 GPU 内存分配策略（10% 而非 95%），在单个 24GB GPU 上并行运行最多 9 次推理。
  - 调整 “bucket size”，使模型输入长度匹配实际蛋白序列长度，减少填充开销。
- **AlphaFold3 模型改进点**：
  - 采用 Pairformer 模块和扩散生成模型替代 AlphaFold2 的 Evoformer。
  - 推理时降低 seed 数量（发现单个 seed 即可获得最佳结果）。

### 3. 算法流程（文字概述）
1. 输入待预测的免疫受体序列；  
2. 使用精简数据库生成 MSA（由 JackHMMER 完成）；  
3. 进入 AF3 推理阶段，利用 Pairformer + Diffusion 模块生成三维结构；  
4. 输出结构并计算 RMSD 与实验结构的偏差；  
5. 结果通过多种 seed 对比与评分机制（ipTM + pTM + disorder 等）进行验证。

---

## 三、实验设计与比较方法

- **数据集**：
  - TCR 数据集：来自 VDJ 数据库的 3,213 条非冗余序列（用于构建数据库），另有 77 条实验结构（PDB）用于验证。
  - 抗体数据集：来自 SAbDab 的 2,490 条参考序列用于数据库构建，另有 525 条精准结构用于验证。
- **Benchmark 对比方法**：
  - 与当前主流或同类工具对比：**TCRBuilder2**, **Boltz-2**, **ABodyBuilder2**。
- **评估指标**：
  - 使用 RMSD（全原子、Cα、骨架、CDR 级别）衡量结构预测精度，统计显著性（Mann–Whitney–Wilcoxon 测试）。
  - Pearson 相关系数用于评估模型稳定性。

---

## 四、资源与算力

- **硬件配置**：
  - 使用单台 **Dell Precision 3680**，配备 **NVIDIA RTX A4500 Ada Generation GPU（24 GB）**。
  - CPU：8 核用于并行化 MSA 计算。
- **算力消耗**：
  - 抗体模型：单 seed 平均耗时约 30 秒；10 seeds 耗时约 170 秒。
  - TCR 模型：单 seed 耗时约 40 秒。
  - 相较原始 AF3 流程（约 17 分钟），实现 **约 45 倍加速**。
- **训练时长**：文中无自定义训练，仅进行推理优化。

---

## 五、实验数量与充分性

- 多层验证：
  - MSA 收敛分析（500 次随机序列顺序重排试验）。
  - RMSD 对比及统计显著性检验（多达数百结构的评估）。
  - 多 seed 实验（多达 20 种随机种子）。
  - GPU 推理参数对比实验。
- **充分性评价**：
  - 实验覆盖 TCR 与 Ab 两大免疫受体家族，包含 MSA、推理、对比、参数消融和并行优化的系统分析。
  - 实验客观性较高，使用独立验证集并排除训练集重叠。
  - 小部分验证集规模（如 TCR 仅 77 个结构）略受限，但代表性良好。

---

## 六、主要结论与发现

- 使用 <3% 的 UniRef90 序列即可维持 AlphaFold3 的预测准确度。  
- 对免疫受体结构预测的 RMSD 保持在近实验分辨率范围（多数 CDR 区域 RMSD <1Å）。  
- AF3 排名分数与实际结构精度相关性较低，不宜作为模型优选指标。  
- 单 seed 即可达到最佳精度，增加推理轮次无性能提升。  
- 推理阶段优化可达 3.6 倍加速，整体运行时间减少至原流程的约 **1/45**。  
- 模型性能与 Boltz2、TCRBuilder2 等主流方法相当或略优，尤其对 CDR1α 与 CDRH3 区域表现更佳。

---

## 七、优点与创新亮点

- **方法层面**：
  - 通过“数据库精简 + 参数优化”实现对 AF3 的轻量化改造，无需额外训练。
  - 保持模型精度同时极大提高可扩展性，适合大规模免疫受体库结构预测。
- **实验层面**：
  - 严格区分训练集与验证集，保证结果客观。
  - 系统消融分析充分，验证了 MSAs 对不同蛋白族群的必要性差异。
- **应用价值**：
  - 为免疫学、抗体工程和癌症治疗设计提供可行的高通量结构建模方案。

---

## 八、不足与局限性

- **数据覆盖**有限：TCR 验证集数量较小，难以全面评估模型在极端可变序列上的表现。  
- **评分机制不足**：AF3 的 ranking 分数与 CDR 精度弱相关，模型筛选需额外校正。  
- **推理硬件依赖**：GPU 并行加速效果依赖具体显存容量，对低算力用户不够友好。  
- **免疫受体泛化**风险：精简数据库尽管提高效率，但可能丧失少数稀有结构的进化线索。  
- **方法适用性**：目前仅验证在抗体与 TCRs 两类蛋白上，其他多亚家族（如 MHC、激酶）尚未系统测试。

---

（完）
