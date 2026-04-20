---
title: Decoding Single-Cell Omics of Perturbation Responses Using DeSCOPE
title_zh: 利用 DeSCOPE 解码单细胞组学的扰动响应
authors: "Wu, P., Wei, H., Li, Y., Zheng, X., Zhou, C., Hu, X., Wang, C."
date: 2026-04-15
pdf: "https://www.biorxiv.org/content/10.64898/2026.04.13.718147v1.full.pdf"
tags: ["query:virtcell"]
score: 9.5
evidence: 预测跨转录组和表观遗传图谱的遗传扰动反应
tldr: 本文提出DeSCOPE，一种轻量级条件变分自编码器，用于预测单细胞在基因扰动下的多组学响应，解决了当前模型泛化性不足的问题。通过在基因及细胞类型外分布情景下的系统验证，DeSCOPE展现出优异的预测性能，能够高效支持多基因组合扰动分析并助力治疗靶点设计。
source: biorxiv
selection_source: fresh_fetch
figures_json: "[{\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-04-13-718147-v1/fig-001.webp\", \"caption\": \"Fig. 2| DeSCOPE enables prediction of transcriptomic perturbation responses for unseen genes. a, Benchmarking performance on perturbation responses of unseen genes. Overlap@50, overlap ratio of top 50 DE genes; Pearson Δ, Pearson correlation between predicted and true expression changes across\", \"page\": 6, \"index\": 1, \"width\": 871, \"height\": 694}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-04-13-718147-v1/fig-002.webp\", \"caption\": \"Fig. 4|DeSCOPE enables double gene perturbation prediction in different settings. a, Train-test data split categories for two-gene perturbations.\", \"page\": 11, \"index\": 2, \"width\": 871, \"height\": 922}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-04-13-718147-v1/fig-003.webp\", \"caption\": \"Fig. 5| DeSCOPE enables cross-modal prediction of chromatin accessibility perturbations. a, Comparison of DeSCOPE and EpiAgent across five single-gene perturbation scATAC-seq datasets (GM12878, K562, MCF7, K562_1, K562_2). Scatter plots show Pearson correlation, Pearson Δ, and MAE between predicted and observed accessibility profiles for held-out perturbation genes; each point represents a single perturbation.\", \"page\": 14, \"index\": 3, \"width\": 869, \"height\": 1118}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-04-13-718147-v1/fig-004.webp\", \"caption\": \"Fig. 1|Overview of DeSCOPE. DeSCOPE takes scRNA-seq or scATAC-seq data as input. For scRNAseq, gene expression matrices are normalized and log-transformed prior to modeling. For scATAC-seq, peaks are mapped to cis-regulatory elements (cCREs) using the EpiAgent vocabulary, followed by term frequency-inverse document frequency (TF-IDF) transformation and selection of the top k regulatory elements. The framework is implemented as a cVAE, in which perturbation gene embeddings derived from ESM2 are incorporated as conditioning variables to align latent distributions of control and perturbed cells via a KL divergence objective, while the decoder reconstructs perturbation-specific cellular states\", \"page\": 4, \"index\": 4, \"width\": 871, \"height\": 731}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-04-13-718147-v1/fig-005.webp\", \"caption\": \"Fig. 3| DeSCOPE enables prediction of transcriptomic perturbation responses for unseen celltypes. a, Evaluation of perturbation responses of unseen cell types in zero-shot scenarios.\", \"page\": 9, \"index\": 5, \"width\": 871, \"height\": 1081}]"
motivation: 现有计算方法难以在跨基因和细胞类型的扰动响应预测中保持稳健性与泛化性。
method: 采用轻量级条件变分自编码器框架集成多组学数据进行预测。
result: DeSCOPE在跨基因和细胞类型的单细胞扰动响应预测中显著优于基线模型，尤其在未见过的基因和细胞类型上表现突出。
conclusion: DeSCOPE提供了一个泛化性强的多组学虚拟细胞模型，可用于指导细胞表型改变的治疗靶点设计。
---

## 摘要
破解细胞对基因扰动的响应是建立基因调控网络模型并理解改变细胞表型机制的基础。然而，当前的计算方法往往无法优于简单的基线模型，显示出其在泛化性和鲁棒性方面的关键瓶颈。本文提出了 DeSCOPE，这是一种轻量级条件变分自编码器框架，可用于预测涵盖转录组、表观基因组及更广泛多模态景观的基因扰动响应。我们在两个具有挑战性的分布外设置 —— 未见的基因和未见的细胞类型 —— 下，对 DeSCOPE 在多样化数据集上进行了系统基准测试。DeSCOPE 在未见基因的场景中独特地超越了简单的基线模型；同时，在未见细胞类型场景下实现了显著提升的性能，并且微调所需的扰动基因数量更少。最后，DeSCOPE 在预测多基因组合扰动方面表现出更优的性能。总体而言，DeSCOPE 作为一种通用的多模态虚拟细胞模型，可高效地指导改变细胞表型的治疗靶点设计。DeSCOPE 可在 https://github.com/wanglabtongji/DeSCOPE 获取。

## Abstract
Deciphering cellular responses to genetic perturbations is fundamental to modeling gene regulatory networks and understanding mechanisms that change cellular phenotypes. However, current computational approaches often fail to outperform simple baseline models, highlighting a critical bottleneck in their generalizability and robustness. Here, we present DeSCOPE, a lightweight conditional variational autoencoder framework for predicting genetic perturbation responses spanning transcriptomic, epigenomic, and broader multi-modal landscapes. We systematically benchmarked DeSCOPE across diverse datasets under two challenging out-of-distribution settings: unseen genes and unseen cell types. DeSCOPE uniquely surpasses simple baselines in the unseen gene scenario, and achieves substantially improved performance for unseen cell types while requiring fine-tuning with far fewer perturbed genes. Finally, DeSCOPE demonstrates superior performance in predicting combinatorial multi-gene perturbations. Overall, DeSCOPE serves as a versatile multi-modal virtual cell model that can effectively guide the design of therapeutic targets that change cellular phenotypes. DeSCOPE is available at https://github.com/wanglabtongji/DeSCOPE.

---

## 论文详细总结（自动生成）

# 利用 DeSCOPE 解码单细胞组学扰动响应 —— 论文详细总结

---

## 一、核心问题与研究背景

- **研究动机**：  
  破解细胞对基因扰动的响应是理解基因调控网络与细胞表型变化机制的关键。然而，现有计算模型（如 GEARS、STATE、scGPT、EpiAgent 等）在跨基因或跨细胞类型的预测中普遍缺乏**鲁棒性与泛化能力**，许多情况下甚至不如简单的线性或均值基线模型。

- **核心问题**：  
  如何构建一个既轻量、可扩展，又能在**“未见基因”与“未见细胞类型”**情形下稳定预测单细胞扰动响应的模型。

- **研究目标**：  
  设计一个通用框架，能够整合多组学（包括转录组和表观组）数据，跨模态预测细胞在基因扰动后的状态，从而推动虚拟细胞（virtual cell）模型的发展。

---

## 二、方法论：DeSCOPE 框架

### 1. 核心思想
- 提出 **DeSCOPE (Decoding Single-Cell Omics of Perturbation Responses)**，一种**基于条件变分自编码器（cVAE）**的轻量模型；
- 目标：在给定未扰动（control）细胞状态和目标扰动基因时，预测扰动后的单细胞状态；
- 通过结构化的潜变量空间解耦控制态与扰动态的分布，实现**更好的分布外泛化（out-of-distribution generalization）**。

### 2. 关键技术机制
- **输入与条件变量**：  
  将 **控制态细胞特征** 与 **扰动基因的嵌入表示** 共同输入模型；
- **基因嵌入源自 ESM2（蛋白语言模型）**：  
  - 提取每个基因的蛋白氨基酸序列；
  - 经 ESM2 生成 5120 维向量，之后经过线性投影与归一化；
- **潜变量对齐机制**：  
  - 控制状态生成“先验分布”；  
  - 扰动状态生成“后验分布”；  
  - 通过 KL 散度正则项，使两者在潜空间对齐，保留控制与扰动间的连续生物学关系；
- **模型结构简洁**：  
  编码器和解码器均为轻量多层感知机（MLP）；
- **优化目标**：  
  - 重构损失：MSE  
  - KL 散度：对齐先验与后验  
  - 总损失：  
    $$ L = \alpha \cdot \text{MSE} + \beta \cdot D_{KL}(q(z|x_{pert},g)\|p(z|x_{ctrl},g)) $$

### 3. 模型推理流程
- **训练阶段**：控制态与扰动态同时输入，用真实数据估计潜变量分布；
- **推理阶段**：仅使用控制态与目标基因嵌入推算潜变量，再重构扰动态。

---

## 三、实验设计与对比体系

### 1. 主要数据集
- **单基因扰动转录组（scRNA-seq）**：  
  K562_ESSENTIAL、RPE1、H1、HepG2、Jurkat（共五个数据集）；
- **多基因扰动（双扰动）**：  
  Norman (Science 2019) 数据集；
- **表观组扰动（scATAC-seq）**：  
  GM12878、K562 (两批)、MCF7 共五个数据集（Spear-ATAC 或 CRISPR-sciATAC）。

### 2. 基准任务场景
- 未见基因 (unseen gene) 泛化；
- 未见细胞类型 (unseen cell type) 泛化；
- 双基因组合扰动 (combination perturbation)；
- 跨模态（转录组→表观组）预测。

### 3. 对比方法
| 分类 | 模型 |
|------|------|
| 深度模型 | CPA, STATE, scGPT, GEARS |
| 基线模型 | Linear, PerturbMean |
| 其他 | MatchMean（组合扰动），EpiAgent（ATAC基线） |

### 4. Benchmark 指标
- Differential gene overlap (Overlap@50/@100)  
- Pearson Δ / Δ20  
- MAE（平均绝对误差）  
- Perturbation Discrimination Score (PDS)

---

## 四、资源与计算消耗

- 模型在单 GPU 下运行（作者未明示 GPU 型号）；
- 默认配置：
  - 批量大小 (batch) = 64  
  - 每个阶段训练 20 个 epoch  
  - 优化器 AdamW，学习率从 0→1e-4 的线性暖启动 + 余弦衰减；
- 与其他模型在 **K562_ESSENTIAL** 数据上的耗时比较（每 epoch，batch=64）：
  | 模型 | 时间(s) | GPU显存(MB) |
  |------|----------|--------------|
  | GEARS | 660 | 3680 |
  | scGPT | 1464 | 25762 |
  | CPA | 271 | 1034 |
  | **DeSCOPE** | **40** | **1404** |

> **结论**：DeSCOPE 在保证性能的同时，显著降低计算开销与显存消耗。

---

## 五、实验数量与充分性

- **scRNA-seq 场景（单基因）**：5个数据集 × 6种模型；
- **跨细胞类型实验**：3个跨迁移方向（K562→HepG2/RPE1/Jurkat），涵盖 zero-shot 与 few-shot；
- **双基因扰动**：3种组合可见性设定（Combo_seen0/1/2）；
- **scATAC-seq 模态扩展**：5个独立 dataset；
- **Leave-one-out (LOO) 迁移策略**：用于跨数据线学习。  
  → 总计十余组实验，配合若干消融与可视化（潜空间、reconstruction 分布）。  

**充分性评价**：涵盖多模态、多任务、多数据源的验证，指标体系完备，实验评估较客观、公平。

---

## 六、主要结论与发现

1. **跨基因预测**：  
   DeSCOPE 是唯一能在 unseen gene 任务上持续超越 PerturbMean 的模型。  
   LOO 迁移显著增强泛化性能。
2. **跨细胞类型预测**：  
   零样本条件下仍有困难，但在 few-shot（如 50-shot）中显著超越现有 SOTA；
   需少量目标细胞微调即可快速适配。
3. **双基因扰动**：  
   实现接近或优于 MatchMean 的性能，可正确识别不同遗传交互类型（Additive、Synergistic、Suppressive）。
4. **跨模态扩展（ATAC）**：  
   DeSCOPE 对表观组扰动预测精度（Pearson Δ = 0.3–0.65）远高于 EpiAgent (<0.1)，
   能准确预测活化与抑制区域的方向。
5. **总体性能**：  
   兼具高准确性、强泛化和高计算效率，在虚拟细胞建模任务上具备通用性。

---

## 七、优势与亮点

- ✅ **轻量高效**：基于 MLP 的 cVAE 架构，训练耗时仅需数十分之一；
- ✅ **结构可解释性强**：潜空间对齐机制契合生物学连续性；
- ✅ **跨模态扩展性**：同框架可平滑处理 scRNA 与 scATAC；
- ✅ **简单迁移策略**：LOO transfer 实现跨细胞系共享学习；
- ✅ **低样本友好**：在 few-shot 模式下快速适应；
- ✅ **生物学一致性**：保持扰动与控制态的局部流形结构。

---

## 八、不足与局限

- ⚠ **零样本跨细胞泛化受限**：无目标细胞数据时性能仍不稳定；
- ⚠ **scATAC 数据鲁棒性不足**：高 dropout 导致 PerturbMean 可达相似表现；
- ⚠ **特定基因嵌入依赖**：依赖 ESM2 提供蛋白级表征，非蛋白编码基因难以覆盖；
- ⚠ **缺乏 in vivo 验证**：当前验证均在 in vitro 系统；
- ⚠ **模型额外与外部先验结合未深入探索**：如 GO 图谱或结构耦合基因网络。

---

**（完）**
