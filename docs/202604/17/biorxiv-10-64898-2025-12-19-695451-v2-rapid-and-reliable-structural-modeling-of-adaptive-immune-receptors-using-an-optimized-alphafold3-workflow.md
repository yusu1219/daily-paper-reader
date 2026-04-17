---
title: Rapid and Reliable Structural Modeling of Adaptive Immune Receptors Using an Optimized AlphaFold3 workflow
title_zh: 利用优化的 AlphaFold3 工作流程对适应性免疫受体进行快速且可靠的结构建模
authors: "Jann, A., Perez, M. A. S., Zoete, V."
date: 2026-04-15
pdf: "https://www.biorxiv.org/content/10.64898/2025.12.19.695451v2.full.pdf"
tags: ["query:gentcr"]
score: 9.0
evidence: 优化的AlphaFold3用于T细胞受体（TCR）结构建模
tldr: 本研究针对AlphaFold3在免疫受体结构建模中的应用提出改进方案，通过优化多序列比对数据集与推理流程，将建模速度提升约45倍，同时仍维持近实验级的预测精度，为抗体和TCR高通量建模与免疫机制研究提供高效工具。
source: biorxiv
selection_source: fresh_fetch
figures_json: "[{\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2025-12-19-695451-v2/fig-001.webp\", \"caption\": \"Figure 1. a) General overview of AF3 original workflow and our AF3 variant workflow, along with running 74 time of the corresponding AF3 MSA and inference phases. The original AF3 uses 4 databases to build the 75 MSA input while AF3 variant uses a much smaller database named UniRef90-TCR or UniRef90-Ab. b) 76 Process used to build the reduced Uniref90-TCR/Ab databases, by sequentially generating MSAs for 77 individual TCRs using JackHMMER and the UniRef90 database, and aggregating the resulting sequences. 78\", \"page\": 4, \"index\": 1, \"width\": 990, \"height\": 825}]"
motivation: 由于抗体和T细胞受体在免疫反应中至关重要，亟需更高效的结构预测方法支撑大规模研究与药物设计。
method: 作者系统评估AlphaFold3中多序列比对组成与推理阶段数量，并基于精简的UniRef90子集优化工作流程。
result: 研究表明，通过优化AlphaFold3的多序列比对组成和推理阶段次数，可显著加快抗体和T细胞受体结构预测的速度且保持高精度。
conclusion: 该优化工作流为快速、可靠的免疫受体结构预测奠定基础，助力免疫学研究与药物发现。
---

## 摘要
AlphaFold（AF）是一种基于深度学习的蛋白质建模方法，通过在蛋白质结构预测中普遍实现接近实验精度的成果，彻底改变了结构生物学的研究。AF 的一个重要应用是抗体（Abs）和 T 细胞受体（TCRs）的建模——它们是细胞免疫的关键介质，其结构特异性是癌症、感染和自身免疫性疾病免疫反应的基础。在本研究中，我们通过系统分析 MSA（多序列比对）组成及推理阶段的数量对预测精度和计算效率的影响，评估了 AF3 的性能。通过使用精简的 UniRef90 子集，我们提出了一种约快 45 倍的高精度 AF3 工作流程变体，专为抗体和 TCR 受体结构域建模优化，能够在适用于高通量免疫学研究的规模下实现快速、可靠的结构预测。我们的研究结果为加速治疗性发现以及深入理解免疫识别的分子机制提供了基础。

## Abstract
AlphaFold (AF), a deep-learning based protein modelling approach, has revolutionized structural biology by generally achieving near-experimental accuracy in protein structure prediction. An impactful application of AF is the modelling of antibodies (Abs) and T-cell receptors (TCRs), key mediators of cellular immunity, whose structural specificity underlies responses in cancer, infection, and autoimmune diseases. In this work, we analyse AF3 performance by systematically examining how MSA composition and the number of inference phases affect prediction accuracy and computational efficiency. Using reduced UniRef90 subsets, we present a ~45-fold accelerated and highly accurate variant of the AF3 workflow specifically optimized for the modelling of the Abs and TCRs receptor domains, enabling rapid, reliable structural predictions at a scale suitable for high-throughput immunological studies. Our findings provide a foundation for faster therapeutic discovery and deeper molecular mechanism understanding of immune recognition.

---

## 论文详细总结（自动生成）

# 利用优化的 AlphaFold3 工作流程对适应性免疫受体进行快速且可靠的结构建模 — 中文结构化总结

---

## 一、研究背景与核心问题

### 研究动机
- **蛋白质结构预测革命性进展**：AlphaFold（AF）系列已实现接近实验级精度的蛋白质结构预测，推动了结构生物学和药物发现。
- **免疫受体的特殊性**：抗体（Antibody, Ab）与 T 细胞受体（T-cell receptor, TCR）是适应性免疫系统的核心组成部分。它们具有高度序列多样性和复杂的互补决定区（CDR）结构，对癌症免疫、感染防御、自免疾病等有决定性作用。
- **问题与挑战**：
  - AlphaFold3（AF3）中最耗时部分是 **多序列比对（MSA）生成阶段**，占总运行时间的约90%以上。
  - 在大规模免疫受体研究中，结构预测效率是明显瓶颈。

### 研究目标
作者旨在优化 AF3 工作流程，使其能：
- 快速、高效建模大量抗体与 TCR；
- 保持接近实验精度的预测；
- 适用于高通量免疫学与结构药理学研究。

---

## 二、方法论：优化的 AlphaFold3 工作流程

### 核心思想
- **通过优化多序列比对数据库与推理参数**，降低 AF3 运行时间，同时保持预测精度。
- 替换掉 AF3 默认的庞大 MSA 数据库，用更精简、针对性强的子集。

### 技术要点
1. **MSA 阶段优化**：  
   - 创建三个新的数据库：
     - **UniRef-TCR**：从 3,213 个 TCR 序列生成，仅约占 UniRef90 全库的 3%。  
     - **UniRef-Ab**：从 2,490 个参考抗体生成。  
     - **UniRef-TextMining**：通过关键词（抗体/TCR相关）从 UniRef90 文本头中提取，共 41,055 条序列。
   - 通过 JackHMMER 依次生成每条序列的 MSA 并聚合结果，构建精简子集。

2. **推理阶段优化**：  
   - 调整 GPU 内存分配（由默认95%降至10%），使能在单张 GPU 上并行运行 9 个推理。  
   - 定制 **bucket size** 匹配输入长度，减少填充 tokens，从而减少无效计算。  
   - 仅使用单个随机种子（seed）代替多次采样，减少冗余计算。

3. **工作流程对比**：
   - 原始 AF3 使用四大数据库（UniRef90, MGnify, BFD, UniProt）。  
   - 优化版仅用定制子数据库，大幅加快 MSA 阶段并简化推理参数设置。

4. **算法体系保持一致**：
   - 保留 **Pairformer 模块** 与 **Diffusion-based Generative Model**。
   - 主体结构更新机制不变，只优化输入与推理过程。

---

## 三、实验设计

### 数据集与验证集
- **TCR 数据**：
  - 来自 VDJdb（共 3,213 条非冗余序列，涵盖约200种抗原特异性）。
  - 测试集包含 77 条在 AlphaFold3 训练集外、与 MHC结合的 TCR。
- **抗体数据**：
  - 来自 SAbDab 数据库（共 2,490 条参考序列用于数据库构建；525 条独立验证结构）。
  - 确保与 AF3 训练数据不重叠，分辨率 ≤ 3 Å。

### Benchmark 与对比方法
- 对比基准：
  - **原始 AF3 工作流**（使用完整数据库）。
  - **无 MSA 版本**。
  - **三种精简数据库版本（UniRef-TCR, UniRef-Ab, UniRef-TextMining）**。
- 外部对比方法：
  - **Boltz2**：通用蛋白建模工具（基于扩散模型）。  
  - **TCRBuilder2**：专用于 TCR 高效建模的轻量化方法。  
  - **AbodyBuilder2**：专用于抗体结构建模的工具。

### 评估指标
- **RMSD（Root Mean Square Deviation）**：
  - 在整体结构与各个 CDR 环节计算 RMSD，与实验结构比对。
  - 并通过 Pearson 相关系数与 Mann–Whitney–Wilcoxon 测试评估统计显著性。

---

## 四、资源与算力

- **硬件环境**：
  - 一台 Dell Precision 3680 工作站；
  - GPU：**NVIDIA RTX A4500 Ada Generation (24 GB)**；
  - CPU：单核或最多使用 8 核；
  - RAM 约 40 GB（在多推理任务时）。

- **运行性能**：
  - 原始 AF3：约 11–17 分钟/模型；
  - 优化版 AF3：**仅需 10–40 秒**生成完整模型；
  - GPU 并行推理最高可达 9 任务同时执行。

- **训练资源**：论文未提及重新训练，仅基于已发布的 AlphaFold3 权重作快速推理。

---

## 五、实验数量与充分性

- 共执行 **多种类型实验**：
  1. MSA 数据库分析与子集收敛实验（针对 TCR 与抗体各进行 100 次随机顺序测试）。  
  2. 结构精度测试：使用 77 个 TCR 与 525 个抗体结构对照实验结构。  
  3. 多种数据库配置（共四种）。  
  4. 种子数量消融实验（1–20 seeds）。  
  5. 与 Boltz2、TCRBuilder2、AbodyBuilder2 的精度与计算速度对比。  
  6. GPU 参数优化实验（bucket 与 memory fraction）。

- **充分性与公平性**：  
  数据来源广泛、覆盖主流免疫受体类型；验证集与训练集严格区分；统计方法规范。  
  对比方法选择合理，实验充分体现改进的有效性。

---

## 六、主要结论与发现

1. **性能提升**：
   - MSA 阶段加速约 **45 倍**；
   - 推理阶段再提速 **1.5–3.6 倍**；
   - 总建模时间从十几分钟缩短到几十秒。

2. **精度保持**：
   - 新数据库下的结构预测 RMSD 与原版 AF3 差异**无显著性**（p > 0.05）。  
   - 在最难的 CDR 区域（如 TCR CDR3β、Ab CDRH3）仍保持近实验分辨率。

3. **种子分析结论**：
   - 使用单一推理种子已可获得高精度结果；增加种子数量不提升质量。

4. **与其他方法比较**：
   - AF3（含优化版）与 Boltz2、TCRBuilder2 在准确率上相当；  
   - 优化版在速度与通用性方面全面领先。

5. **适用性与推广**：
   - 可推广至其他结构富集的蛋白家族（如激酶、蛋白酶、MHC 复合物）。

---

## 七、研究优点

- **针对性强**：专为免疫受体优化，数据库极度压缩但保留关键演化信息。
- **计算效率显著提升**：端到端速度提升多个数量级。
- **方法简便**：无需修改 AF3 模型，仅替换数据库与参数。
- **结果鲁棒性高**：子集数据库与原版结果具有 >0.75 的 RMSD 相关系数。
- **资源友好**：桌面级 GPU 即可完成大规模建模。

---

## 八、不足与局限

- **MSA依赖仍存在**：完全去除 MSA 时，TCR 模型精度显著下降，反映演化信息仍不可或缺。
- **模型评分问题**：AF3 默认 ranking score 与 CDR 精度相关性低，导致模型选优不准确。
- **训练偏差**：TCR 数据的实验结构数量少于抗体，导致泛化性能略有差异。
- **局限性场景**：当前优化针对免疫受体，其他蛋白家族尚需重新验证。
- **硬件依赖性未全面测试**：性能评估集中在一款 GPU 型号，尚未覆盖不同硬件环境。

---

**（完）**
