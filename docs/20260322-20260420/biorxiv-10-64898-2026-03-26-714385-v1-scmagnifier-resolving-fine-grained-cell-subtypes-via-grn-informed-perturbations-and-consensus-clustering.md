---
title: "scMagnifier: resolving fine-grained cell subtypes via GRN-informed perturbations and consensus clustering"
title_zh: scMagnifier：通过基因调控网络（GRN）驱动的扰动与共识聚类解析细粒度细胞亚型
authors: "He, Z., Kangning, D."
date: 2026-03-28
pdf: "https://www.biorxiv.org/content/10.64898/2026.03.26.714385v1.full.pdf"
tags: ["query:virtcell"]
score: 9.0
evidence: 利用基因调控网络指导的计算机模拟扰动来揭示细胞亚群
tldr: scMagnifier是一种基于基因调控网络(GRN)的单细胞RNA测序分析框架，通过模拟转录因子扰动并结合共识聚类，有效放大细微表达差异，提升细胞亚型识别精度，并可应用于空间转录组数据揭示肿瘤细胞亚群。
source: biorxiv
selection_source: fresh_fetch
figures_json: "[{\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-03-26-714385-v1/fig-001.webp\", \"caption\": \"Fig. 5 The integration of scMagnifier and STAGATE identifies tumor cell 827 subtypes and their spatial organization in ovarian cancer. a. Spatial visualization 828 of the ovarian cancer dataset. Left two panels: cell-type annotations and spatial layer 829 annotations provided with the dataset. Right two panels: clustering results from 830 STAGATE alone (Leiden, resolution=0.3) and from scMagnifier combined with 831 STAGATE. b. H&E-stained image highlighting the specific regions analyzed in the 832 dataset used for our experiments. c. Bubble plot of the top 5 differentially expressed 833\", \"page\": 25, \"index\": 1, \"width\": 941, \"height\": 1177}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-03-26-714385-v1/fig-002.webp\", \"caption\": \"Fig. 1 Overview of scMagnifier. a. scMagnifier takes the gene expression matrix and 763 a basic gene regulatory network as inputs, and derives the initial clustering results 764 using a standard clustering pipeline. b. scMagnifier obtains distinct clustering results 765 by performing TF perturbations on cluster-specific gene regulatory networks. c. The 766 output of scMagnifier is a consensus clustering result visualized on UMAP and 767 rpcUMAP embeddings. d. scMagnifier first constructs cluster-specific GRN based on 768 the basic GRN and initial clustering results. e. scMagnifier systematically perturbs 769 candidate TF genes and propagates their effects through cluster-specific GRN to 770 generate an ensemble of post-perturbation clustering results. f. scMagnifier integrates 771 perturbation-driven clustering results with expression-based similarities to construct a 772 combined cell–cell distance matrix, enabling consensus clustering and the generation 773 of a rpcUMAP. 774\", \"page\": 21, \"index\": 2, \"width\": 941, \"height\": 574}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-03-26-714385-v1/fig-003.webp\", \"caption\": \"Fig. 2 Benchmarking of scMagnifier. a. Bar plots illustrating the performance of 778 seven algorithms on four single-batch datasets, evaluated using the Adjusted Rand 779 Index (ARI) and Normalized Mutual Information (NMI). b. Bar plots of clustering 780 performance on two multi-batch datasets for seven batch-correction methods, alone 781 or combined with scMagnifier. c. UMAP and rpcUMAP visualization of BMMC dataset 782 clustering via scVI (ARI=0.62) and scMagnifier+scVI (ARI=0.66). The red circle 783 highlights a myeloid lineage-enriched compartment containing CD14+ Mono, CD16+ 784 Mono, cDC2 and G/M prog cells. A zoomed view contrasts this compartment on 785 standard UMAP versus rpcUMAP. d. rpcUMAP visualization of CENPE and MKI67 786 gene expression in Cluster 0 of the BMMC dataset, obtained using the 787 scVI+scMagnifier workflow. e. UMAP visualization of BCL11A perturbation in the 788 BMMC dataset using the scMagnifier+scVI workflow. The leftmost panel shows the 789 sum of absolute expression changes for BCL11A and its target genes across cells. The 790 four panels on the right display UMAP visualizations of post-perturbation clustering 791 results as the perturbation fold change increases. 792\", \"page\": 22, \"index\": 3, \"width\": 941, \"height\": 893}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-03-26-714385-v1/fig-004.webp\", \"caption\": \"Fig. 3 scMagnifier uncovers hidden heterogeneity among MAIT/Th1-Th17 cell 795 populations. a. Comparison of original Leiden clustering and scMagnifier results. Left: 796 UMAP visualization of standard Leiden clustering (resolution = 0.75). Middle: UMAP 797 and rpcUMAP visualization of scMagnifier clustering. The connecting lines denote the 798 positional correspondence of clusters identified by scMagnifier between the UMAP and 799 rpcUMAP embedding spaces. The red circle highlights the focal clusters (Cluster 2 and 800 Cluster 16). Right: rpcUMAP visualization of cell type distributions in the dataset. b. 801 Sankey diagram showing the correspondence among original Leiden clusters, 802 scMagnifier clusters and cell-type annotations. c. Bubble plot of the top 10 differentially 803 expressed genes (DEGs) for each cluster, among cluster 2, cluster 16 and the 804 remaining Th1/Th17 cells. d. UMAP heatmaps showing the expression of CD8A, 805 NKG7, NCR3, and PRF1 in cluster 2 and cluster 16. e. KEGG pathway enrichment 806 analysis of cluster 2 and cluster 16, showing the top 10 most significantly enriched 807 pathways. f. Bar plot of the top 10 TF genes ranked by importance scores in cluster 808 16. 809\", \"page\": 23, \"index\": 4, \"width\": 941, \"height\": 677}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-03-26-714385-v1/fig-005.webp\", \"caption\": \"Fig. 4 scMagnifier detects rare immune cell populations in lung adenocarcinoma 812 datasets. a. UMAP and rpcUMAP visualizations of scMagnifier results on the 813 EBUS_10 dataset, highlighting the R1 and R2 clusters. The connecting lines denote 814 the positional correspondence of R1 and R2 between the UMAP and rpcUMAP 815 embedding spaces. b. Violin plots showing the expression profiles of the top 15 DEGs 816 individually selected from R1 and R2, across R1, R2 and the remaining cell-type-817 annotated cells. c. Heatmap of gene expression for the top 10 upregulated genes 818 selected from each of the four clusters (R1, R2, MALT B cells and GC B cells in the 819 DZ). d. UMAP and rpcUMAP visualizations of scMagnifier results on the LUNG_N30 820 dataset, highlighting the R3 clusters. e. Bubble plot showing Jaccard coefficient values 821 between R1 and clusters of the remaining cells grouped by cell-type annotations. f. 822 Heatmap of gene expression for the top 10 upregulated genes selected from each of 823 the two clusters (R3 and NK). g. UMAP heatmaps showing the expression of ID2, IFNG, 824 GIMAP7 and TBC1D10C in R3 and NK cells. 825\", \"page\": 24, \"index\": 5, \"width\": 922, \"height\": 948}]"
motivation: 现有单细胞RNA测序难以区分细微细胞亚型，亟需放大其潜在转录差异的新方法。
method: 该方法通过对候选转录因子进行模拟扰动，利用特定簇的GRN传播效应，并整合多次聚类结果实现亚型识别。
result: scMagnifier在单批次和多批次基准测试中均显著提升了细胞亚型识别的准确度，并成功揭示癌症细胞亚型的空间分布。
conclusion: scMagnifier显著提高了单细胞及空间转录组分析中细胞亚型解析的分辨率和稳定性。
---

## 摘要
在单细胞RNA测序（scRNA-seq）数据中解析细粒度的细胞亚型仍然具有挑战性，因为它们微弱的转录差异常常被技术噪声和数据稀疏性所掩盖。在此，我们提出了scMagnifier，一种利用基因调控网络（GRN）指导的计算机模拟扰动的共识聚类框架，用以放大微弱的转录差异并揭示潜在的细胞亚群。scMagnifier对候选转录因子（TF）进行扰动，将扰动效应通过特定聚类的GRN传播，以模拟扰动后的表达谱，并将多个扰动条件下的聚类结果整合为稳定的亚型划分。此外，scMagnifier引入了调控扰动共识UMAP（rpcUMAP），这是一种考虑扰动的可视化方法，可在细胞亚型之间提供更清晰的分隔，并指导最佳聚类数量的选择。在单批与多批基准测试中，scMagnifier持续提升了细粒度细胞类型识别的分辨率和准确性。值得注意的是，当与STAGATE等空间聚类方法结合时，scMagnifier可与空间转录组学工作流程兼容，并有效揭示卵巢癌中肿瘤细胞亚型及其空间组织结构。

## Abstract
Resolving fine-grained cell subtypes in single-cell RNA sequencing (scRNA-seq) data remains challenging, as their subtle transcriptional differences are often obscured by technical noise and data sparsity. Here, we present scMagnifier, a consensus clustering framework that leverages gene regulatory network (GRN)-informed in silico perturbations to amplify subtle transcriptional differences and uncover latent cell subpopulations. scMagnifier perturbs candidate transcription factors (TFs), propagates perturbation effects through cluster-specific GRNs to simulate post-perturbation expression profiles, and integrates clustering results across multiple perturbations into stable subtype assignments. Additionally, scMagnifier introduces regulatory perturbation consensus UMAP (rpcUMAP), a perturbation-aware visualization that provides clearer separation between cell subtypes and guides the selection of the optimal number of clusters. In both single-batch and multi-batch benchmarks, scMagnifier consistently improves the resolution and accuracy of fine-grained cell type identification. Notably, when integrated with spatial clustering methods such as STAGATE, scMagnifier is compatible with spatial transcriptomics workflows and effectively reveals tumor cell subtypes and their spatial organization in ovarian cancer.

---

## 论文详细总结（自动生成）

# 论文总结：**scMagnifier：通过GRN驱动的扰动与共识聚类解析细粒度细胞亚型**

---

## 一、研究背景与核心问题

- **研究动机**：单细胞RNA测序（scRNA-seq）极大地推动了细胞异质性的研究，但现有聚类算法在识别**细粒度细胞亚型**方面仍存在困难。微弱的转录差异通常被数据稀疏性与技术噪声掩盖，导致近似状态的细胞难以区分（如免疫细胞活化状态或肿瘤亚克隆）。
- **理论背景**：生物学上，细胞的可区分性不仅体现在基因表达水平，也体现在**基因调控网络（GRN）**的差异。不同细胞即使表达谱相似，也可能对同一转录因子的扰动产生不同响应。
- **核心问题**：如何利用GRN结构信息与虚拟扰动方式放大细胞间潜在的调控差异，从而提高细粒度细胞亚型划分的解析度。

---

## 二、方法论：scMagnifier 的核心思想与技术框架

### 1. 总体思想
scMagnifier 是一个 **基于 GRN 的共识聚类框架**，通过模拟转录因子（TF）的扰动作用来放大细胞间差异，并整合多个扰动实验得到稳定聚类。

### 2. 技术流程概述
- **输入**：原始基因表达矩阵（GEM） + 基础 GRN。
- **步骤**：
  1. **初始聚类**：使用常规算法（Leiden 或 Louvain）对 scRNA-seq 数据预聚类。
  2. **构建簇特异性 GRN**：基于 CellOracle 框架，以各聚类内 TF 与靶基因表达关系剪枝得到 cluster-specific GRN。
  3. **TF扰动仿真**：
     - 对候选TF模拟上调/下调；
     - 使用线性传播模型迭代计算下游靶基因表达变化；
     - 将扰动结果叠加至原表达矩阵形成“后扰动”表达矩阵。
  4. **生成扰动集成结果**：每次扰动产生一次聚类结果，形成“扰动驱动聚类集合”。
  5. **共识聚类整合**：
     - 将多个聚类结果转换为 one-hot 表示；
     - 计算细胞间的组合距离矩阵（含表达距离 + 扰动距离，加权系数默认 0.8）；
     - 基于该矩阵构建 KNN 图并再次进行共识聚类。
  6. **rpcUMAP 可视化**：
     - 使用组合距离作为 UMAP 输入，形成“调控扰动共识 UMAP”，提升聚类间可分性。
  7. **簇合并与阈值控制**：
     - 基于簇质心距离与最小簇大小阈值自动合并过细或噪声簇，得到最终稳定亚型。

### 3. 数学要点（非公式化说明）
- **扰动传播**：使用 TF–靶基因权重矩阵进行迭代乘法，模拟三轮（n=3）的多层调控影响。
- **距离融合**：将扰动驱动的余弦距离与嵌入空间的欧几里得距离归一化后按权重叠加。
- **簇合并策略**：利用质心间距离的中位数 * 0.75 作为合并阈值，既保持分辨率又避免过分碎片化。

---

## 三、实验设计与 benchmark 内容

### 1. 数据集类型
共分析与验证多个场景：
- **单批次数据**：四个肺腺癌 scRNA-seq 数据集。
- **多批次数据**：两个公开集（胰腺数据集、BMMC骨髓样本）。
- **空间转录组数据**：卵巢癌空间表达数据（SPATCH 平台）。
- **特定细胞群分析**：UPN19_pre数据集（研究MAIT与Th1/Th17群体）。

### 2. 对比方法
- 标准聚类：Leiden、Louvain；
- 深度生成模型：scVI；
- 批次校正整合：Harmony、Scanorama、BBKNN；
- 共识聚类基线：SC3s。

### 3. 指标
- 采用 **Adjusted Rand Index (ARI)** 与 **Normalized Mutual Information (NMI)** 评估聚类一致性。
- 辅助评估：差异表达分析、功能通路富集、Jaccard 系数等。

---

## 四、资源与算力说明

- 文中未提供 GPU 型号、数量或训练时间等硬件信息；
- 所有计算基于 Python 与 Scanpy + CellOracle 实现；
- 仅说明算法可扩展至 Harmony、scVI 等低维嵌入空间，因此推测计算量适中，无深度训练过程。

👉 **结论**：论文未披露算力与训练配置。

---

## 五、实验数量与充分性

- **单批次基准测试**：4 个肺癌数据集，7 种算法对比。
- **多批次整合测试**：2 个数据集 × 6 种批次校正方法组合。
- **亚群解析案例**：MAIT/Th1-Th17 混合群体细化分析。
- **稀有细胞检测案例**：EBUS_10 与 LUNG_N30 数据。
- **空间转录组整合案例**：卵巢癌空间组织分析。

总计涵盖约 **9 套独立实验场景**，包含对比、可视化与功能验证，实验格式公正且覆盖充分。

---

## 六、主要结论与发现

- scMagnifier 在所有 benchmark 中 **ARI/NMI 均显著优于传统聚类与共识方法**；
- **rpcUMAP 明显提升细胞群分离度**，有助于确定“最佳聚类数目”；
- 虚拟扰动可 **放大生物学相关的转录差异**（如 BCL11A 对 pDC 的作用与文献一致）。
- 成功解析：
  - MAIT/Th1-Th17 混合群体的功能异质性；
  - 识别多个稀有亚群（如活化型 B 细胞、特殊 NK 细胞）；
  - 空间转录组中揭示卵巢癌高侵袭区域，与H&E形态及IGF2信号一致。

---

## 七、优点与创新点

- **理论创新**：首次在聚类框架中引入“GRN驱动的模拟扰动”概念，用于放大微弱调控差异。
- **方法稳健**：通过多次扰动结果共识融合，提高聚类稳定性。
- **兼容性强**：可与多种批次校正或空间聚类方法（Harmony、STAGATE）直接结合。
- **可解释性高**：扰动机制与TF重要性打分提供生物学推理链路。
- **可视化增强**：rpcUMAP提供扰动感知的嵌入空间，改善细胞边界清晰度。

---

## 八、不足与未来方向

- **生物真实性限制**：扰动仅基于GRN线性传播，未充分模拟真实生物扰动的非线性动态。
- **算力细节缺失**：缺乏计算资源报告，难评估可扩展性。
- **数据类型局限**：目前仅限于转录组层面的分析，未验证在多组学（ATAC-seq、蛋白组）场景下的有效性。
- **聚类合并参数影响结果**：阈值设定（如最小簇比例）需手动调整，不同场景下结果可能敏感。
- **缺少系统性消融实验**：未详述扰动次数、传播深度等超参对性能的影响。

---

**（完）**
