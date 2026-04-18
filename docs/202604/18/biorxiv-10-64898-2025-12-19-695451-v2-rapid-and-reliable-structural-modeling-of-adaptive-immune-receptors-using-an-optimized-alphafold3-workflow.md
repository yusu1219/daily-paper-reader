---
title: Rapid and Reliable Structural Modeling of Adaptive Immune Receptors Using an Optimized AlphaFold3 workflow
title_zh: 使用优化的 AlphaFold3 工作流程对适应性免疫受体进行快速且可靠的结构建模
authors: "Jann, A., Perez, M. A. S., Zoete, V."
date: 2026-04-15
pdf: "https://www.biorxiv.org/content/10.64898/2025.12.19.695451v2.full.pdf"
tags: ["query:gentcr"]
score: 8.0
evidence: 使用优化的AlphaFold3工作流进行TCR结构建模
tldr: 本研究针对AlphaFold3在免疫受体建模中的应用，系统分析MSA组成及推理参数对预测的影响，并提出优化流程。优化后显著提升了建模速度与准确度，为抗体与TCR的大规模结构预测提供高效解决方案。
source: biorxiv
selection_source: fresh_fetch
figures_json: "[{\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2025-12-19-695451-v2/fig-001.webp\", \"caption\": \"Figure 1. a) General overview of AF3 original workflow and our AF3 variant workflow, along with running 74 time of the corresponding AF3 MSA and inference phases. The original AF3 uses 4 databases to build the 75 MSA input while AF3 variant uses a much smaller database named UniRef90-TCR or UniRef90-Ab. b) 76 Process used to build the reduced Uniref90-TCR/Ab databases, by sequentially generating MSAs for 77 individual TCRs using JackHMMER and the UniRef90 database, and aggregating the resulting sequences. 78\", \"page\": 4, \"index\": 1, \"width\": 990, \"height\": 825}]"
motivation: AlphaFold性能卓越，但在抗体和T细胞受体建模中速度和效率需提升。
method: 通过调整MSA数据库子集、优化推理阶段和参数，实现模型加速与精度提升。
result: 优化后AlphaFold3可在保持高准确度的同时，实现约45倍的MSA阶段加速和3.6倍推理提速。
conclusion: 该优化版AlphaFold3流程加速了免疫受体建模，为快速治疗研究和免疫机制解析奠定基础。
---

## 摘要
AlphaFold（AF）是一种基于深度学习的蛋白质建模方法，在蛋白质结构预测中通常能达到接近实验精度，从而彻底革新了结构生物学。AF 的一个重要应用是对抗体（Abs）和 T 细胞受体（TCRs）进行建模，这些作为细胞免疫的关键介质，其结构特异性决定了在癌症、感染和自身免疫性疾病中的免疫应答。在本研究中，我们系统分析了 AF3 的性能，探讨了多序列比对（MSA）组成、推理阶段数以及推理参数对预测精度和计算效率的影响。通过使用精简的 UniRef90 子集，我们在 AF3 的 MSA 阶段实现了约 45 倍的加速，并通过优化参数使 AF3 的推理速度提高了最多 3.6 倍。我们提出了一种高精度的 AF3 工作流程变体，专为抗体和 TCR 受体结构域建模优化，能够以适合高通量免疫学研究的规模实现快速、可靠的结构预测。我们的研究成果为加速治疗性药物发现和深入理解免疫识别的分子机制奠定了基础。

通过改进关键步骤，我们使 AlphaFold3 在建模特定免疫蛋白时的速度提高了约 40 倍。

## Abstract
AlphaFold (AF), a deep-learning based protein modelling approach, has revolutionized structural biology by generally achieving near-experimental accuracy in protein structure prediction. An impactful application of AF is the modelling of antibodies (Abs) and T-cell receptors (TCRs), key mediators of cellular immunity, whose structural specificity underlies responses in cancer, infection, and autoimmune diseases. In this work, we analyse AF3 performance by systematically examining how MSA composition, number of inference phases and inference parameters affect prediction accuracy and computational efficiency. We present an acceleration of [~]45-fold of the AF3 MSA phase using reduced UniRef90 subsets, combined with up to a 3.6-fold increase in AF3 inference speed through optimized parameters. We provide a highly accurate variant of the AF3 workflow specifically optimized for the modelling of the Abs and TCRs receptor domains, enabling rapid, reliable structural predictions at a scale suitable for high-throughput immunological studies. Our findings provide a foundation for faster therapeutic discovery and deeper molecular mechanism understanding of immune recognition.

TeaserBy improving key steps in the process, we made AlphaFold3 about 40 times faster at modeling specific immune proteins

---

## 论文详细总结（自动生成）

# 使用优化的 AlphaFold3 工作流程对适应性免疫受体进行快速且可靠的结构建模  
（Rapid and Reliable Structural Modeling of Adaptive Immune Receptors Using an Optimized AlphaFold3 workflow）  

---

## 一、研究动机与核心问题

- **研究背景：**  
  AlphaFold 系列模型已在蛋白质结构预测领域取得近实验级的精度，成为结构生物学突破性成果。然而，AlphaFold3（AF3）在应用于抗体（Ab）与 T 细胞受体（TCR）建模时仍面临**计算效率低与 MSA（多序列比对）阶段耗时严重**的问题。  
- **核心问题：**  
  MSA 阶段占据 AF3 总计算时间的 90% 以上，成为高通量研究中的主要瓶颈。对于免疫学中常需建模成千上万受体域结构的任务，这一瓶颈严重限制了应用。  
- **研究目标：**  
  提出一套专门针对抗体与 TCR 的 AF3 优化工作流程，在保持原始预测精度的前提下显著提升速度，使其适用于大规模免疫受体结构建模。

---

## 二、方法论与技术方案

- **核心思想：**  
  通过两个关键层面的优化最大限度提高 AF3 效率：  
  1. **MSA 阶段优化：** 使用免疫蛋白专属的精简数据库子集代替完整 UniRef90；  
  2. **推理阶段优化：** 调整推理参数并利用 GPU 并行化，减少模型生成时间。

- **主要技术步骤：**
  1. **创建专用数据库子集：**  
     - 利用 JackHMMER 对 3213 条 TCR 序列和 2490 条抗体序列进行逐个 MSA。  
     - 聚合所用序列，仅占 UniRef90 总量的 <3%。  
     - 构建了三个数据库：`UniRef-TCR`、`UniRef-Ab` 和 `UniRef-textmining`。  
     - 这些子集包含几乎全部免疫相关序列（>98.6% 具有免疫 GO 分类）。  
  2. **MSA 阶段替换：**  
     使用上述子集替代 AF3 通常使用的四个大型数据库（UniRef90、MGnify、BFD、UniProt），保持同样的接口与流程。
  3. **推理阶段优化：**  
     - 将 GPU 预分配内存比例调低至 10%，实现多推理并行（最多 9 个）。  
     - 针对输入蛋白长度定制 bucket size，消除填充开销。  
     - 在同等硬件上，推理阶段整体加速约 1.5~3.6 倍。
  4. **算法思想：**  
     AF3 通过 Pairformer + Diffusion 模块迭代更新单体和配对表示，不依赖深 MSA；因此方法的优化重点放在输入数据规模与推理参数控制上，而非模型架构本身。

---

## 三、实验设计与对比体系

- **数据集与验证集：**
  - **TCR 集：**  
    从 VDJ 数据库中选取 3213 条非冗余序列用于 MSA 分析；从 PDB 中抽取 77 条新近结构（不在训练集内）作为验证集。  
  - **抗体集：**  
    从 SAbDab 数据库中提取 2490 条多样化序列用于 MSA 构建，另外 525 条独立抗体结构用于验证性能。  

- **对比方法与基线：**
  - AlphaFold3 原始工作流（完整数据库）。  
  - 自建精简数据库版本（UniRef-TCR、UniRef-Ab、UniRef-textmining）。  
  - 无 MSA 输入版本。  
  - 其他建模软件：Boltz2、TCRBuilder2（用于 TCR）；ABodyBuilder2（用于抗体）。  
  - 统计指标：RMSD（整体与各 CDR 区段）、速度比、Pearson 相关系数。

- **Benchmark 场景：**  
  通过对比各模型生成结构与实验结构的 RMSD 差异确定预测精度，并评估运行时间、参数敏感性。

---

## 四、资源与算力

- **硬件配置：**
  - 单机系统：Dell Precision 3680 工作站。  
  - GPU：NVIDIA RTX A4500 Ada Generation（24GB 显存）。  
  - CPU：至多使用 8 核。  
  - GPU 内存预分配比例调为 10%（允许 9 个推理并行）。  

- **算力说明：**
  - MSA 阶段：使用 6 个 CPU 并发执行（通过 Slurm 任务队列）。  
  - 推理阶段：单 GPU 计算。  
  - **训练阶段未涉及**（仅模型推理加速无重新训练）。  
  - 运行时间：  
    - 原始 AF3：约 15–17 分钟；  
    - 优化版：约 40 秒（TCR）或 10 秒（抗体）。

---

## 五、实验数量与充分性

- 共进行了 **数十次系统性实验**，主要包括：
  1. **MSA 聚合与数据库收缩实验**（>500 次随机顺序堆叠分析以验证收敛性）；  
  2. **AF3 变体性能测试**（TCR 与抗体各四种 MSA 配置）；  
  3. **多种种子（1–20 seeds）比较实验**；  
  4. **推理参数优化实验**（bucket 尺寸与并行度影响）；  
  5. **与三种竞争方法的对比（Boltz2、TCRBuilder2、ABodyBuilder2）**。  

- **充分性与公平性：**
  - 所有验证集均严格排除 AlphaFold3 训练集结构。  
  - 多次随机采样与统计学检验（Mann-Whitney-Wilcoxon 两侧检验、p-value 标注）。  
  - 对照实验覆盖 MSA、有无 MSA、不同参数与多竞争工具，设计较为全面公正。

---

## 六、主要结论与发现

1. **MSA 优化：**  
   使用 UniRef-TCR/Ab 子集可实现 **约 45× MSA 阶段加速**，占用的序列量不到原数据库的 3%，精度仍保持近实验级。  
2. **推理优化：**  
   GPU 并行与 bucket 调整使 AF3 推理阶段提升 **1.5–3.6×**。  
3. **预测精度：**  
   - RMSD 与原始 AF3 高度相关（Pearson >0.75），尤其在 CDR3 区段维持稳定性能。  
   - 抗体 CDRH3 与 TCR CDR3β 仍为最难建模区段，但误差与原始模型相近。  
4. **模型评分不足：**  
   发现 AF3 默认 ranking score 与 CDR RMSD 相关性较弱（r ≈ −0.25），无法可靠筛选最佳模型。  
5. **快速推理与单种子验证：**  
   使用单一种子即可获得高质量预测，多种子采样无额外收益。  
6. **综合性能：**  
   优化版 AF3 在精度上与原模型无显著差异，显著超越专门免疫预测工具在速度和泛化能力上的表现。

---

## 七、研究优点

- **系统性优化：** 从流程角度而非模型架构层面提升效率，方法简洁实用，易于迁移。  
- **数据驱动的数据库简化策略：** 通过迭代 MSA 聚合确定最小充分序列集，体现科学可重复的过程。  
- **全面对照实验：** 覆盖不同阶段（MSA、推理）及多类竞争算法。  
- **免疫专属性能验证：** 强调抗体与 TCR 在结构变异性和免疫应用中的特殊性。  
- **高通用性与可扩展性：** 研究方法可推广至其他蛋白家族（如蛋白激酶、MHC 复合物等）。

---

## 八、不足与局限

- **MSA 仍需要：**  
  尽管精简后大幅提速，TCR 建模仍依赖部分 MSA 信息，完全 MSA-free 效果显著下降。  
- **模型评分不足：**  
  默认 AF3 ranking score 在免疫受体场景下无法准确反映模型质量，后续需重新定义评分函数。  
- **数据覆盖限制：**  
  TCR 实验结构远少于抗体，可能影响模型在此类复杂构象上的泛化。  
- **硬件依赖性：**  
  GPU 并行优化与内存调整策略较依赖具体显卡型号，推广至小型设备仍需验证。  
- **未涉及训练阶段优化：**  
  本研究仅限于推理效率提升，未探讨如何在训练端进一步减负或改进模型通用性。

---

**（完）**
