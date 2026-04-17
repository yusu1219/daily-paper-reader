---
title: "MHCXGraph: A Graph-Based approach to detecting T cell receptor cross-reactivity"
title_zh: MHCXGraph：一种基于图的 T 细胞受体交叉反应性检测方法
authors: "Simoes, C. D. M. S., Maidana, R. L. B. R., De Assis, S. C., Guerra, J. V. d. S., Ribeiro-Filho, H. V."
date: 2026-04-10
pdf: "https://www.biorxiv.org/content/10.64898/2026.04.07.717034v1.full.pdf"
tags: ["query:gentcr"]
score: 9.0
evidence: 基于图的方法检测T细胞受体交叉反应性
tldr: 本文提出 MHCXGraph，一种基于图的计算方法，用于识别肽-MHC 结构间的保守和关键免疫区域，旨在突破序列分析对 T 细胞受体交叉反应性研究的限制，通过多案例验证显示其在结构保守性检测和计算性能方面的优势，为免疫疗法和疫苗设计提供新的支持。
source: biorxiv
selection_source: fresh_fetch
figures_json: "[{\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-04-07-717034-v1/fig-001.webp\", \"caption\": \"Figure 1: Schematic workflow of the MHCXGraph package. (A) Schematic workflow illustrating the main steps and algorithms of the method. (B) Detailed view of the triad representation, highlighting its features and attributes. (C) Detailed view of the coherent frame graph generation step, illustrating the operation of the depth-first search (DFS) algorithm on the association graph. Local clique searches supporting the DFS in identifying coherent nodes are also shown. Green and red lines connecting nodes indicate whether pairs of association nodes satisfy the coherence condition, i.e., whether all corresponding nodes respect the global distance threshold across input structures. (D) Schematic overview of the package execution modes.\", \"page\": 3, \"index\": 1, \"width\": 979, \"height\": 696}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-04-07-717034-v1/fig-002.webp\", \"caption\": \"Figure 2: Illustrative example of the MHCXGraph dashboard. This example represents an output dashboard from an MHCXGraph run in screening mode. In this case, the MAGE-A3 melanoma-related peptide presented by HLA-A*01 is compared to a self-peptide derived from the titin protein and to a peptide derived from an influenza protein, both bound to the same HLA. The dashboard highlights, in the upper panel, the graph frames of the first component for each comparison, and in the bottom panel, the projection of the graphs onto the corresponding oriented 3D structures. On the left, a set of metadata and parameters can be accessed and visualized.\", \"page\": 5, \"index\": 2, \"width\": 979, \"height\": 495}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-04-07-717034-v1/fig-003.webp\", \"caption\": \"Figure 3: MHCXGraph analysis of different experimentally validated cross-reactivity case studies. (A) MHCXGraph analysis of 11 different HLAs without peptides, using a node granularity of Cα, an edge threshold of 10 Å, and local and global distance difference thresholds of 1.0 and 2.0, respectively. The heatmap on the left presents the pairwise comparison between each HLA based on the coverage-based similarity index. The values within each heatmap cell correspond to the number of unique nodes found across all frames of all components of the association graph. The diagonal represents twice the number of nodes in each input graph, corresponding to the maximum number of nodes that could be identified in a theoretical association graph of the same input protein. Dendrograms were built using the UPGMA hierarchical clustering method. In the center, the frames from the first two components of the association graph are shown. These originate from the multiple-analysis run mode applied to HLA-A only. The graph projection onto the superposed 3D structures is shown on the right, where nodes are depicted by residue side chains. (B) The same MHCXGraph analysis as in (A), but applied to a set of peptides presented by HLA-A*02. Asterisks on the heatmap labels (MELANA, BST2, and IMP2) indicate peptides that were determined to be recognized by the same Mel5 TCR. (C) MHCXGraph analysis in multiple-analysis run mode of cross-reactive HIV-1 peptides bound to different MHC-II alleles. Only the association graph and its projection onto the superposed 3D structures are shown. The node granularity used was the centroid of all residue atoms, with an edge threshold of 8.5 Å and with the use of the RSA feature in the triad. Local and global distance difference thresholds were set to 2. All analyses presented here were performed using an RSA threshold of 0.1 to define exposed nodes.\", \"page\": 6, \"index\": 3, \"width\": 783, \"height\": 995}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-04-07-717034-v1/fig-004.webp\", \"caption\": \"Figure 4: MHCXGraph runtime and memory usage analysis. (A) Runtime analysis of MHCXGraph in multiple mode using two datasets: the Diverse HLA dataset, comprising structures with different MHC-I alleles and peptides, and the Single HLA dataset, comprising structures from the same HLA-A*02:01 allele bound to different peptides. (B) Peak memory usage analysis of MHCXGraph in multiple mode. (C) Runtime analysis of MHCXGraph in screening mode. A linear trend line is presented in all analyses. For all analyses, MHCXGraph was executed using Cα node granularity and an edge threshold of 8.5 Å, without incorporating RSA into triad features. Local and global distance difference thresholds were set to 1 Å and 2 Å, respectively.\", \"page\": 7, \"index\": 4, \"width\": 979, \"height\": 297}]"
motivation: 研究旨在解决传统序列分析在识别 T 细胞受体交叉反应性中的局限性。
method: 采用图结构分析方法整合多种 pMHC 结构信息，并通过三种操作模式实现灵活和可解释的分析。
result: 在多个案例研究中，MHCXGraph 成功发现了超越序列相似性的结构保守性区域，展现了其可靠性和可扩展性。
conclusion: MHCXGraph 能有效捕捉肽-MHC 复合物的结构保守性，为 T 细胞交叉反应性研究和相关疗法设计提供了新工具。
---

## 摘要
T 细胞受体（TCR）对主要组织相容性复合物（MHC）呈递的多种肽的识别是一个关键的自然现象，使得 T 细胞库能够应对广泛的抗原。尽管其对免疫反应具有重要性，T 细胞的交叉反应性在新型 T 细胞治疗的开发中仍是一大挑战。本研究提出了 MHCXGraph，这是一种基于图的计算方法，用于识别结合于 MHC 分子（pMHC）的多种肽结构中保守且免疫学相关的区域。该方法提供三种操作模式，并允许用户定义参数，可根据具体科研需求灵活配置，同时通过用户友好的界面输出完全可解释的结果。我们在三种案例研究中评估了 MHCXGraph，包括与经典 MHC I 类分子、MHC II 类分子结合的肽，以及未结合的 HLA 等位基因，结果表明该方法能够捕捉超越序列相似性的保守结构决定因素。通过将结构信息与高效的基于图的分析相结合，MHCXGraph 在保持计算可扩展性的同时克服了基于序列的方法的主要局限性。总体而言，这些结果表明，MHCXGraph 可方便地整合入用于发现 T 细胞交叉反应性的计算流程中，特别适用于从头设计 pMHC 结合物及基于 T 细胞的疫苗开发。

## Abstract
AO_SCPLOWBSTRACTC_SCPLOWThe T cell receptor (TCR) recognition of multiple peptides presented by the major histocompatibility complex (MHC) is a key natural phenomenon, enabling the T cell repertoire to respond to a broad array of antigens. Despite its importance to the immune response, T cell cross-reactivity poses a major challenge for the development of novel T cell-based therapies. In this study, we present MHCXGraph, a graph-based computational approach for identifying conserved and immunologically relevant regions across multiple structures of peptides bound to MHC molecules (pMHC). Our approach provides three operational modes with user-defined parameters, allowing flexible configuration according to specific scientific needs while delivering fully interpretable results through user-friendly interfaces. We evaluated MHCXGraph across three case studies, including peptides bound to classical MHC Class I, MHC Class II, and unbound HLA alleles, demonstrating its ability to capture conserved structural determinants beyond sequence similarity. By integrating structural information with efficient graph-based analysis, MHCXGraph addresses key limitations of sequence-based methods while maintaining computational scalability. Collectively, these results indicate that MHCXGraph can be readily integrated into computational pipelines for T cell cross-reactivity discovery, especially in the context of de novo pMHC engager design and T cell-based vaccine development.

---

## 论文详细总结（自动生成）

# MHCXGraph：一种基于图的 T 细胞受体交叉反应性检测方法 — 深入总结

---

## 一、研究背景与核心问题

- **研究动机**：  
  T 细胞受体（TCR）能识别由主要组织相容性复合物（MHC）呈递的多种肽，从而形成广泛的免疫反应能力。然而，**TCR 的交叉反应性（cross-reactivity）**既是免疫系统多样性的关键来源，也在免疫疗法开发中带来安全性风险（如非靶向结合）。传统基于**序列相似性**的方法在识别此类交叉反应时常失效，因为结构层面的保守性在免疫识别中更为重要。

- **核心目标**：  
  作者希望构建一种能够在**三维结构层面**揭示肽-MHC 复合体（pMHC）之间保守结构区域的方法，以便更准确地预测 TCR 交叉反应性，从而支持免疫疗法与疫苗设计。

---

## 二、方法论：MHCXGraph 的核心思想与技术细节

- **总体思想**：  
  将多个 pMHC 复合物结构建模为**图结构（Graph）**，节点表示氨基酸残基或其结构中心，边表示结构距离与空间关系。通过图对齐与关联分析，识别不同结构间的**保守作用区域**和潜在的 TCR 结合决定因素。

- **关键步骤与算法流程**：
  1. **图构建阶段**：  
     - 从输入的 pMHC 三维结构中提取结点（例如 Cα 原子或残基质心）。  
     - 基于空间距离（典型阈值 8.5–10 Å）建立边并赋予权重。
  2. **三元特征表示（Triad Representation）**：  
     - 将每个节点及其相邻节点形成三元组特征，包括空间距离、相对溶剂可接触面积（RSA）等。  
     - 有助于局部结构特征的统一计算。
  3. **关联图生成与搜索**：  
     - 构建“关联图”（Association Graph），比较不同结构间节点的匹配关系。  
     - 采用深度优先搜索（DFS）配合局部团簇搜索（local clique search）来确定满足**全局距离阈值**的“相干节点”（coherent nodes）。
  4. **运行模式**：  
     - **Screening 模式**：快速筛选两个或多个 pMHC 结构间的相似区域。  
     - **Multiple 模式**：多结构并行比较，用于大规模分析。  
     - **Single 模式**：单结构的内部比较与分析。  

- **算法特性**：  
  - 采用 **UPGMA 层次聚类**整合结构相似度结果。  
  - 接口可视化输出，包括图框架（frame graph）与 3D 对应投影。  
  - 参数高度可调（节点粒度、距离阈值、RSA 阈值等）。

---

## 三、实验设计与数据集

- **测试场景**：  
  作者针对三类典型结构进行了验证：
  1. 未结合肽的 MHC-I 结构（11 种不同 HLA）。  
  2. 不同肽与同一 HLA-A*02:01 结合的复合物。  
  3. 来自 HIV-1 的 MHC-II 结合肽（存在已验证的交叉反应性）。

- **数据来源**：  
  主要来自公开的结构数据库（如 PDB）或已报道的交叉反应性案例。

- **对比方式（Benchmark）**：  
  并未与其他计算方法进行算法性能对比，而是从生物学合理性角度进行验证，比如：
  - 能否在已知交叉反应性肽对中发现共性结构区域；
  - 是否能在不同 HLA 结构中发现保守的框架节点。

---

## 四、资源与算力使用

- **算力说明**：  
  论文主要为计算结构分析，而非深度学习模型训练，因此：
  - 未提及具体 GPU 或高性能计算环境。  
  - 程序运行采用 Python/C++ 实现，能够在常规工作站上执行。  
  - 图计算性能测试显示运行时间与节点数量呈线性关系。

- **结论**：  
  算力要求低，未涉及 GPU 加速，也未报告训练时长或硬件规格。

---

## 五、实验数量与充分性

- **实验数量**：  
  - 三组主要案例研究（MHC-I 无肽、MHC-I 结合肽、MHC-II 结合肽）。  
  - 每组包含多个结构（例如 11 种 HLA、多个肽配对）。  
  - 对每个场景执行多模式分析和可视化验证。

- **充分性与公平性**：  
  - 虽然覆盖了 MHC-I 与 MHC-II 两大类别，但实验仍以结构示例为主。  
  - 没有统计性能（如灵敏度/特异性）量化指标，也未与序列方法直接对比。  
  - 结论主要依赖结构观察与可解释性展示，较为定性。

---

## 六、主要结论与发现

- MHCXGraph 能有效发现多个 pMHC 结构中的**空间保守区域**。  
- 相似性检测结果不仅仅依赖序列一致性，而是捕捉到结构对应关系，可揭示 TCR 交叉识别的潜在决定因素。  
- 在多结构分析模式下，方法在计算效率与存储占用方面具有良好线性扩展性。  
- 可直接嵌入到 TCR–pMHC 识别或疫苗设计的计算流程中，提升结构层面的解释能力。

---

## 七、优点与创新点

- **结构维度创新**：从序列走向三维结构相似性，是本领域的重要突破。  
- **图模型可解释性强**：输出结果包括可视化的相干节点与对应三维投影。  
- **算法灵活性高**：三种运行模式适应不同规模分析任务。  
- **参数透明、用户定义**：研究者可根据需要调整距离阈值、粒度等。  
- **计算性能稳定**：时间和内存随输入结构规模线性增长，具备可扩展性。

---

## 八、不足与局限性

- **定量验证不足**：缺少与已有方法（如结构比对、能量评分）直接的数值对比。  
- **实验覆盖有限**：目前仅在少量结构案例中测试，未大规模评估普适性。  
- **生物学解释偏定性**：未建立与功能实验（如 TCR 结合实验）的一一对应验证。  
- **参数敏感性**：节点粒度、距离阈值的选择可能影响结果稳定性。  
- **应用限制**：在缺乏高分辨率结构数据的情况下，方法效果受限。

---

**（完）**
