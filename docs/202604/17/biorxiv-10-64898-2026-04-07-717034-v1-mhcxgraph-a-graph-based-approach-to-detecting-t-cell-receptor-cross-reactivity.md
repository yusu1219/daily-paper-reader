---
title: "MHCXGraph: A Graph-Based approach to detecting T cell receptor cross-reactivity"
title_zh: MHCXGraph：一种基于图的 T 细胞受体交叉反应性检测方法
authors: "Simoes, C. D. M. S., Maidana, R. L. B. R., De Assis, S. C., Guerra, J. V. d. S., Ribeiro-Filho, H. V."
date: 2026-04-10
pdf: "https://www.biorxiv.org/content/10.64898/2026.04.07.717034v1.full.pdf"
tags: ["query:gentcr"]
score: 8.0
evidence: 基于图的方法检测免疫组库中的T细胞受体交叉反应性
tldr: 本文提出MHCXGraph，一种基于图的计算方法，用于识别MHC结合肽的保守和免疫相关区域，以解析T细胞受体的交叉反应性。该方法融合结构信息，支持多模式分析，提升跨MHC体系结构特征识别能力，为T细胞疗法和疫苗设计提供新工具。
source: biorxiv
selection_source: fresh_fetch
figures_json: "[{\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-04-07-717034-v1/fig-001.webp\", \"caption\": \"Figure 1: Schematic workflow of the MHCXGraph package. (A) Schematic workflow illustrating the main steps and algorithms of the method. (B) Detailed view of the triad representation, highlighting its features and attributes. (C) Detailed view of the coherent frame graph generation step, illustrating the operation of the depth-first search (DFS) algorithm on the association graph. Local clique searches supporting the DFS in identifying coherent nodes are also shown. Green and red lines connecting nodes indicate whether pairs of association nodes satisfy the coherence condition, i.e., whether all corresponding nodes respect the global distance threshold across input structures. (D) Schematic overview of the package execution modes.\", \"page\": 3, \"index\": 1, \"width\": 979, \"height\": 696}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-04-07-717034-v1/fig-002.webp\", \"caption\": \"Figure 2: Illustrative example of the MHCXGraph dashboard. This example represents an output dashboard from an MHCXGraph run in screening mode. In this case, the MAGE-A3 melanoma-related peptide presented by HLA-A*01 is compared to a self-peptide derived from the titin protein and to a peptide derived from an influenza protein, both bound to the same HLA. The dashboard highlights, in the upper panel, the graph frames of the first component for each comparison, and in the bottom panel, the projection of the graphs onto the corresponding oriented 3D structures. On the left, a set of metadata and parameters can be accessed and visualized.\", \"page\": 5, \"index\": 2, \"width\": 979, \"height\": 495}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-04-07-717034-v1/fig-003.webp\", \"caption\": \"Figure 3: MHCXGraph analysis of different experimentally validated cross-reactivity case studies. (A) MHCXGraph analysis of 11 different HLAs without peptides, using a node granularity of Cα, an edge threshold of 10 Å, and local and global distance difference thresholds of 1.0 and 2.0, respectively. The heatmap on the left presents the pairwise comparison between each HLA based on the coverage-based similarity index. The values within each heatmap cell correspond to the number of unique nodes found across all frames of all components of the association graph. The diagonal represents twice the number of nodes in each input graph, corresponding to the maximum number of nodes that could be identified in a theoretical association graph of the same input protein. Dendrograms were built using the UPGMA hierarchical clustering method. In the center, the frames from the first two components of the association graph are shown. These originate from the multiple-analysis run mode applied to HLA-A only. The graph projection onto the superposed 3D structures is shown on the right, where nodes are depicted by residue side chains. (B) The same MHCXGraph analysis as in (A), but applied to a set of peptides presented by HLA-A*02. Asterisks on the heatmap labels (MELANA, BST2, and IMP2) indicate peptides that were determined to be recognized by the same Mel5 TCR. (C) MHCXGraph analysis in multiple-analysis run mode of cross-reactive HIV-1 peptides bound to different MHC-II alleles. Only the association graph and its projection onto the superposed 3D structures are shown. The node granularity used was the centroid of all residue atoms, with an edge threshold of 8.5 Å and with the use of the RSA feature in the triad. Local and global distance difference thresholds were set to 2. All analyses presented here were performed using an RSA threshold of 0.1 to define exposed nodes.\", \"page\": 6, \"index\": 3, \"width\": 783, \"height\": 995}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-04-07-717034-v1/fig-004.webp\", \"caption\": \"Figure 4: MHCXGraph runtime and memory usage analysis. (A) Runtime analysis of MHCXGraph in multiple mode using two datasets: the Diverse HLA dataset, comprising structures with different MHC-I alleles and peptides, and the Single HLA dataset, comprising structures from the same HLA-A*02:01 allele bound to different peptides. (B) Peak memory usage analysis of MHCXGraph in multiple mode. (C) Runtime analysis of MHCXGraph in screening mode. A linear trend line is presented in all analyses. For all analyses, MHCXGraph was executed using Cα node granularity and an edge threshold of 8.5 Å, without incorporating RSA into triad features. Local and global distance difference thresholds were set to 1 Å and 2 Å, respectively.\", \"page\": 7, \"index\": 4, \"width\": 979, \"height\": 297}]"
motivation: T细胞受体识别多肽的交叉反应性挑战了新型T细胞疗法的研发。
method: 采用图模型结合结构信息分析pMHC体系保守区域，提供多种可配置操作模式。
result: 在三种案例研究中，MHCXGraph成功捕获了超越序列相似性的结构保守特征，表现出良好可扩展性。
conclusion: MHCXGraph可无缝整合入计算管线，助力T细胞交叉反应性发现与疫苗设计。
---

## 摘要
T 细胞受体（TCR）识别由主要组织相容性复合体（MHC）呈递的多种肽，是一种关键的自然现象，使得 T 细胞受体谱能够响应广泛的抗原。尽管这种交叉反应性对免疫应答至关重要，但它在新型 T 细胞疗法的开发中也构成了主要挑战。在本研究中，我们提出了 MHCXGraph，一种基于图的计算方法，用于识别多个 MHC 分子结合肽（pMHC）结构中保守且具有免疫学相关性的区域。该方法提供三种运行模式，并允许用户自定义参数，以便根据特定的科学需求灵活配置，同时通过用户友好的界面输出可完全解释的结果。我们在三个案例研究中评估了 MHCXGraph，包括与经典 MHC I 类、MHC II 类以及未结合的 HLA 等位基因结合的肽，结果显示其能够捕捉超越序列相似性的保守结构特征。通过将结构信息与高效的图分析相结合，MHCXGraph 克服了基于序列的方法的关键局限性，同时保持计算可扩展性。总体而言，这些结果表明，MHCXGraph 可轻松集成至 T 细胞交叉反应性发现的计算流程中，尤其适用于新型 pMHC 结合分子设计和基于 T 细胞的疫苗开发。

## Abstract
AO_SCPLOWBSTRACTC_SCPLOWThe T cell receptor (TCR) recognition of multiple peptides presented by the major histocompatibility complex (MHC) is a key natural phenomenon, enabling the T cell repertoire to respond to a broad array of antigens. Despite its importance to the immune response, T cell cross-reactivity poses a major challenge for the development of novel T cell-based therapies. In this study, we present MHCXGraph, a graph-based computational approach for identifying conserved and immunologically relevant regions across multiple structures of peptides bound to MHC molecules (pMHC). Our approach provides three operational modes with user-defined parameters, allowing flexible configuration according to specific scientific needs while delivering fully interpretable results through user-friendly interfaces. We evaluated MHCXGraph across three case studies, including peptides bound to classical MHC Class I, MHC Class II, and unbound HLA alleles, demonstrating its ability to capture conserved structural determinants beyond sequence similarity. By integrating structural information with efficient graph-based analysis, MHCXGraph addresses key limitations of sequence-based methods while maintaining computational scalability. Collectively, these results indicate that MHCXGraph can be readily integrated into computational pipelines for T cell cross-reactivity discovery, especially in the context of de novo pMHC engager design and T cell-based vaccine development.

---

## 论文详细总结（自动生成）

# MHCXGraph：一种基于图的 T 细胞受体交叉反应性检测方法 — 深度总结

---

## 1. 核心问题与研究背景

- **研究动机**：T 细胞受体（TCR）能够识别由主要组织相容性复合体（MHC）呈递的多种肽，这种“交叉反应性”是免疫系统灵活应答的基础。然而，该特性在 **T 细胞疗法和疫苗设计** 中会带来潜在风险，例如非靶向反应或自体免疫反应。
- **研究问题**：现有的主要基于序列比对或能量打分的计算方法 **难以捕捉跨 MHC 体系的结构保守性**，从而无法准确识别 TCR 可能的交叉识别位点。
- **论文目标**：提出一个新的计算框架 **MHCXGraph**，利用结构图模型系统性地解析不同 MHC–肽复合物（pMHC）的空间关系与保守结构特征，从而识别潜在的交叉反应性位点。

---

## 2. 方法论：核心思想与技术实现

- **核心思想**：以图的形式表示和比较多个 pMHC 结构，将每个复合物的氨基酸残基作为节点，将几何关联或接触关系作为边，通过图相似性度量识别结构上保持一致的区域。
  
- **关键技术组件**：
  1. **Triad 表征**：以“残基三联体”为基本分析单元，编码空间与化学特征（如距阈、可溶性暴露度 RSA、侧链取向等）。
  2. **Coherent Frame Graph（CFG）**：通过深度优先搜索（DFS）在关联图中寻找“框架一致性”节点，即结构在多个体系中保持距离阈一致的部分。
  3. **相似性指标**：采用基于覆盖率的相似度量，用于定量比较不同 pMHC 图之间的结构重叠程度。
  4. **运行模式**：
     - *Screening mode*：快速筛选单一结构对比。
     - *Multiple-analysis mode*：对多个结构群进行聚合分析与层级聚类（UPGMA）。
     - *Unbound mode*：研究未结合肽的 HLA 结构保守性。
  
- **计算流程简要**：
  1. 从结构数据库（如 PDB）导入 pMHC 三维结构；
  2. 按指定粒度（如 Cα 原子或残基中心）生成节点和边；
  3. 执行 DFS 和局部团搜索以识别一致节点；
  4. 构造关联图并生成热图、聚类树和结构投影；
  5. 输出结果至可交互 dashboard。

---

## 3. 实验设计与对比

- **数据集与场景**：
  - 三个案例研究：
    1. 多种 **未结合 HLA I** 等位基因（验证结构保守性）。
    2. 多肽绑定于 **HLA-A*02:01**（验证跨肽结构一致性）。
    3. **HIV-1 肽与不同 MHC-II** 等位基因（验证交叉反应性）。
  
- **Benchmark 与对比**：
  - 比较基于序列的传统方法无法识别的潜在保守区域；
  - 使用结构比对和图聚类方式展示了更高分辨率的相似性检测；
  - 通过层级聚类（UPGMA）验证图相似性结果的一一致性和可解释性。

---

## 4. 资源与算力

- **论文未明确说明**使用的计算硬件或 GPU 类型。
- 从图 4 的运行时间与内存分析可推测：
  - 方法在典型桌面级或中小规模 HPC 环境即可运行；
  - 多模式运行的时间呈线性增长，说明算法设计 **计算可扩展性良好**；
  - 内存峰值未出现指数增长，推测可在无 GPU 加速条件下有效执行。

---

## 5. 实验数量与充分性

- **实验组别**：
  - 共开展 **三类主要案例研究**；
  - 每类实验包含 **多个 HLA 或肽组对比分析**；
  - 附带运行时间与内存性能测试。
- **充分性评价**：
  - 覆盖了 MHC I、MHC II、以及未结合体系，数据层面较全面；
  - 未包含大规模统计量或外部验证（如实验 TCR–pMHC 实验数据），因此在实证层面仍有限；
  - 实验设置具有科学合理性与可重复性，但仍属方法验证阶段。

---

## 6. 主要结论与发现

- MHCXGraph 能够：
  - 识别超越序列相似性的保守结构特征；
  - 有效衡量不同 pMHC 体系之间的潜在交叉反应性；
  - 在结构聚类层面揭示 HLA 和肽的功能分布关系；
  - 具备良好的扩展性，可融入免疫信息学工作流。
- 总体结论：该方法为 **结构驱动的交叉反应性分析** 提供了新的计算框架，有潜力指导 TCR 设计、肽筛选与疫苗研发。

---

## 7. 优点与亮点

- **结构层面创新**：突破序列分析局限，捕捉空间保守性。
- **方法灵活性高**：支持多运行模式、参数化配置，适应不同实验需求。
- **图理论结合生物结构**：创新性地用图相似性概念解析免疫识别机制。
- **结果可视化优雅**：通过Dashboard与三维投影展示结构关联性，便于解释。
- **计算效率高**：线性性能趋势，支持大规模数据处理。

---

## 8. 不足与局限

- **数据依赖结构质量**：需要高分辨率的 pMHC 三维结构，限制了广泛应用。
- **未涉及 TCR 直接结合数据**：仅关注 pMHC 层面，未验证实际 TCR 识别事件。
- **算法对参数敏感**：距离阈和暴露度阈的设定可能影响结果稳定性。
- **缺乏生物实验验证**：目前结果仍为计算推测，未来需结合功能实验确认。
- **算力评估不完整**：论文未公开硬件规格与大规模性能情况。

---

（完）
