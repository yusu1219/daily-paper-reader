---
title: Predicting Unseen Gene Perturbation Response Using Graph Neural Networks with Biological Priors
title_zh: 利用具备生物先验的图神经网络预测未见基因扰动反应
authors: "Dip, S. A., Zhang, L."
date: 2026-03-26
pdf: "https://www.biorxiv.org/content/10.64898/2026.03.23.713780v1.full.pdf"
tags: ["query:virtcell"]
score: 9.0
evidence: 利用图学习预测对未知基因扰动的转录响应
tldr: 本文提出PerturbGraph，一个融合生物网络先验的图神经网络框架，用于预测未观察到的基因扰动的转录反应。该方法通过整合蛋白互作网络、功能注释和转录特征，在CRISPR扰动数据上显著优于现有模型，提高了预测准确度和差异表达基因恢复率。
source: biorxiv
selection_source: fresh_fetch
figures_json: "[{\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-03-23-713780-v1/fig-001.webp\", \"caption\": \"Figure 3 Biological reconstruction of perturbation programs. (a–c) Predicted versus observed expression shifts for top differentially expressed genes under representative perturbations showing best (RPL23), median (MYBL2), and challenging (TERF1) cases. (d–e) Quantitative comparison of pathway and topgene overlap between predicted and observed transcriptional programs. (f–h) Local interaction-network responses illustrating propagation of perturbation signals across neighboring genes. (i–k) Recovery of enriched biological pathways from predicted and observed perturbation programs.\", \"page\": 6, \"index\": 1, \"width\": 796, \"height\": 597}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-03-23-713780-v1/fig-002.webp\", \"caption\": \"Table 1 Comparison of baseline models for predicting transcriptional responses of unseen perturbations on held-out test genes. Higher values indicate better performance. Prec@50 reports the mean precision for the top 50 predicted up- and down-regulated genes (values in parentheses).\", \"page\": 4, \"index\": 2, \"width\": 534, \"height\": 494}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-03-23-713780-v1/fig-003.webp\", \"caption\": \"Table 2 Generalization performance on unseen perturbation genes in the Norman CRISPR perturbation dataset.\", \"page\": 4, \"index\": 3, \"width\": 452, \"height\": 269}]"
motivation: 实验性验证所有基因扰动的转录反应不可行，因此需要计算模型预测未见扰动的基因表达变化。
method: 提出基于生物先验知识的图神经网络模型PerturbGraph，整合基因交互网络与功能注释预测扰动响应。
result: "在多项基准测试中，PerturbGraph较传统机器学习和深度模型提升了最高6%的余弦相似度及超过20%的差异基因恢复率。"
conclusion: 融合生物网络与图表示学习能精确预测未见基因扰动的转录反应。
---

## 摘要
预测基因扰动的转录反应是功能基因组学的核心挑战。CRISPR Perturb-seq 实验可测量由靶向扰动引起的基因表达变化，但实验上测试所有可能的扰动仍然不可行。因此，能够推断未观察到扰动反应的计算模型对于大规模功能发现至关重要。我们提出了 PerturbGraph，这是一种基于生物信息的图学习框架，用于通过整合交互网络、功能注释和转录特征来预测未见基因扰动的转录反应。该方法的动机源于扰动效应通过分子交互网络传播，并表现为协调的转录程序这一观察。我们从单细胞 CRISPR 扰动数据出发，构建表示相对于对照细胞的表达变化的扰动特征，并将其投射到一个紧凑的潜在程序空间中，以捕捉稳定的转录变化并减少噪声。每个基因的表示融合了蛋白质-蛋白质交互网络嵌入、网络拓扑统计、基线转录特征以及 Gene Ontology 注释。图神经网络在交互网络中传播信息，从而推断训练中未观察到的基因的扰动程序。在未见扰动的基准测试中，PerturbGraph 在性能上持续优于传统机器学习模型、诸如 scGen 和 CPA 的扰动特定深度学习方法，以及其他图神经网络架构。该模型在余弦相似度上比强树模型基线提高最多 6%，比线性模型提高超过 20%，同时提升了差异表达基因的恢复能力。这些结果表明，将生物交互网络与图表示学习结合，能够准确预测此前未观察到的基因扰动的转录效应。代码已在 https://github.com/Sajib-006/PerturbGraph 上公开发布。

## Abstract
Predicting transcriptional responses to genetic perturbations is a central challenge in functional genomics. CRISPR Perturb-seq experiments measure gene expression changes induced by targeted perturbations, yet experimentally testing all possible perturbations remains infeasible. Computational models that infer responses for unseen perturbations are therefore essential for scalable functional discovery. We introduce PerturbGraph, a biologically informed graph-learning framework for predicting transcriptional responses of unseen gene perturbations by integrating interaction networks, functional annotations, and transcriptional features. Our approach is motivated by the observation that perturbation effects propagate through molecular interaction networks and manifest as coordinated transcriptional programs. Starting from single-cell CRISPR perturbation data, we construct perturbation signatures representing expression shifts relative to control cells and project them into a compact latent program space that captures stable transcriptional variation while reducing noise. Each gene is represented using enriched biological features integrating protein-protein interaction network embeddings, network topology statistics, baseline transcriptional characteristics, and Gene Ontology annotations. A graph neural network propagates information across the interaction network to infer perturbation programs for genes whose effects are not observed during training. Across unseen-perturbation benchmarks, PerturbGraph consistently outperforms classical machine learning models, perturbation-specific deep learning approaches such as scGen and CPA, and alternative graph neural architectures. The model achieves up to 6% improvement in cosine similarity over strong tree-based baselines and more than 20% improvement over linear models while improving recovery of differentially expressed genes. These results show that integrating biological interaction networks with graph representation learning enables accurate prediction of transcriptional effects for previously unobserved genetic perturbations. Code is publicly available at https://github.com/Sajib-006/PerturbGraph.

---

## 论文详细总结（自动生成）

# 《利用具备生物先验的图神经网络预测未见基因扰动反应》论文总结

---

## 一、研究背景与核心问题

- **研究动机**  
  功能基因组学的核心任务之一，是理解基因扰动（如通过 CRISPR 敲除）如何引起转录水平的系统变化。  
  尽管当前 **CRISPR Perturb-seq** 等实验技术能在单细胞水平上测量成千上万种扰动效应，但要覆盖整个人类基因组的所有可能扰动仍极为困难与昂贵。  

- **核心问题**  
  如何在只观察到部分基因扰动反应的情况下，**准确预测未见基因扰动的转录响应**。  
  这类问题是典型的推断任务，其挑战在于：
  - 扰动效应在分子交互网络中呈非线性传播；
  - 单细胞数据噪声较高；
  - 现有模型多侧重细胞水平的表达生成，而非稳定的基因层面调控模式学习。

---

## 二、方法论：PerturbGraph 框架

### 1. 核心思想
- 将扰动效应建模为 **稳定的转录程序（perturbation programs）**，而非直接建模单细胞表达矩阵；
- 通过 **图神经网络（GNN）** 在生物学交互图中进行信息传播；
- 结合多种 **生物先验特征** ——包括蛋白质互作网络结构、基线转录特性、Gene Ontology (GO) 功能嵌入等，形成统一的基因表达预测模型。

### 2. 数据与特征构建
- 从单细胞 CRISPR Perturb-seq 数据构建扰动签名：  
  \[
  \Delta_i = x_i^{pert} - x^{ctrl}
  \]
  表示扰动后与对照组表达均值的差异。
- 再通过 **截断奇异值分解 (Truncated SVD)** 将高维表达矩阵 \( X \) 投影至潜在扰动空间：
  \[
  X \approx H V
  \]
  其中 \( H \) 为低维扰动表示，\( V \) 为转录基表达基。

### 3. 图神经网络建模
- 构造基于 **STRING 数据库** 的生物交互图 \( G=(V,E) \)，节点为基因，边表示功能互作；
- 采用标准 **图卷积网络（GCN）** 信息传播机制：
  \[
  H^{(l+1)} = \sigma( \hat{A} H^{(l)} W^{(l)} )
  \]
  - \( \hat{A} \) 为归一化邻接矩阵；
  - \( W^{(l)} \) 为可学习权重；
  - 输出层表示预测的潜在扰动程序；
- 最终通过重构预测转录响应：
  \[
  \hat{\Delta_i} = \hat{h_i} V
  \]

### 4. 训练与推理流程
- 训练集：观察到的扰动签名；
- 测试集：完全未见扰动基因；
- 优化目标：最小化预测与真实扰动签名间的重构损失；
- 模型仅需一次图前向传播，计算量线性随节点与边增加。

---

## 三、实验设计

### 1. 数据来源
- **Replogle Perturb-seq 数据集（主要基准）**  
  - ~31 万单细胞  
  - 8,563 个基因表达  
  - 1,832 个扰动基因  
  - 提取伪 bulk 的扰动特征  
- **Norman Perturb-seq 数据集（独立测试）**  
  - ~1.5 万单细胞  
  - 18 个单基因扰动

### 2. 对比基准方法
涵盖从线性回归到深度学习再到图模型，共 9 个基线：
- **线性模型**：Lasso, Ridge, ElasticNet  
- **非线性特征模型**：kNN, Random Forest, MLP  
- **扰动专用模型**：scGen, CPA  
- **图神经网络**：GraphSAGE, GAT  
- **本研究模型**：PerturbGraph (GCN backbone)

### 3. 评估指标
- 余弦相似度（Cosine Similarity）  
- Spearman 排名相关系数  
- Precision@k, 方向准确率（DirAcc）  
- 差异表达基因恢复（DE AUROC/AUPRC）

### 4. 数据划分与公平性
- 扰动基因随机划分为 70% 训练、15% 验证、15% 测试；
- 未见基因测试确保 **无数据泄漏**；
- 相同的特征、图结构、参数初始化和随机种子控制，保证可复现性。

---

## 四、资源与算力说明

- 论文未报告使用的 **具体 GPU 型号、数量或训练时长**；
- 仅提到模型“**计算复杂度线性随节点与边增加**，单次前向传播即可完成一轮训练”，表明其在基因组级网络上具有较好可扩展性；
- 训练效率较高，适合中至大型图结构任务。

---

## 五、实验数量与充分性

- **总体实验覆盖：**
  - 2 个 CRISPR 数据集；
  - 9 种基线模型；
  - 完成多次随机种子重复（5 次，报告均值 ± 标准差）；
  - 多种指标全面评估（相关性、方向性、Top-k 精度、DE 精度等）；
  - 进行消融实验（去除/增加生物先验特征）。

- **充分性与公平性：**
  - 实验设计逻辑严谨，数据划分清晰；
  - 消融实验与架构对比验证关键技术贡献；
  - 基线覆盖充分，可认为实验结果 **客观且充分**。

---

## 六、主要结论与发现

- PerturbGraph 在 **未见扰动基因预测** 任务上表现最优：
  - 比最强基线（Random Forest）余弦相似度提升约 6%；  
  - 比线性基线提升超 20%；  
  - 差异表达基因恢复率、方向准确率均显著提高；
- 结合 GO 特征与生物统计后性能进一步提升；
- 模型在图结构中传播扰动信息效果明显，网络距离更近的基因预测更准；
- 模型稳定性强，多次重复实验方差极低（cosine 0.938 ± 0.006）。

---

## 七、研究优点与创新亮点

- **融合多种生物先验知识：**
  - STRING互作图 + GO功能嵌入 + 基线转录统计；
- **方法结构清晰且可复现：**
  - 统一的评估协议与公开代码；
- **重点解决“未见扰动”场景**，填补了多数生成模型无法泛化的空白；
- **良好的可扩展性与生物学解释性：**
  - 输出可还原至基因层面的差异表达模式与通路富集。

---

## 八、局限性与不足

- **预测层级限制：**  
  仅推断扰动层面的聚合响应，未建模单细胞异质性或细胞类型特异性效应。
- **生物网络依赖：**  
  性能高度依赖 STRING 等网络质量与覆盖度，可能对稀疏或新发现基因表现欠佳。
- **无大规模算力评估：**  
  缺乏 GPU/CPU等资源与时间统计，不便比较计算效率。
- **数据广度：**  
  尽管验证了两个数据集，但均来自同一细胞系（K562），跨细胞类型的可迁移性尚未验证。

---

**（完）**
