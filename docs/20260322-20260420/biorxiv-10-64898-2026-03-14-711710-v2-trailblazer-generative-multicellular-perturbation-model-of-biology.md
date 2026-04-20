---
title: "TRAILBLAZER: generative multicellular perturbation model of biology"
title_zh: TRAILBLAZER：生物学中生成式多细胞扰动模型
authors: "Nener, J., Selvamani, P., Badarinarayan, S. S., Chandramohan, N., Grzybowski, A. T."
date: 2026-03-23
pdf: "https://www.biorxiv.org/content/10.64898/2026.03.14.711710v2.full.pdf"
tags: ["query:virtcell"]
score: 10.0
evidence: 生成式多细胞扰动模型，预测对基因或药物扰动的反应
tldr: 本文提出TRAILBLAZER模型，通过多细胞Transformer与结构化潜空间实现对多细胞系统干预反应的生成性预测，克服传统单细胞模型无法泛化的问题，在患者层面上实现了高效、准确的免疫调节剂评估与机制推断。
source: biorxiv
selection_source: fresh_fetch
figures_json: "[{\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-03-14-711710-v2/fig-001.webp\", \"caption\": \"Fig. 2 | Set transformers as attention-based permutation-invariant encoders for cell sets. a, Induced Set Attention based encoders capture all-to-all cell interactions by leveraging induction point attention, while reducing time complexity from O(n2) to O(nm). b, Equal error rate (lower better) for correct treatment classification based on fixed cell set size (50 cells) for cell sets scRNA-seq inferred by networks trained on groups of 1, 5, 50 and 500 cells, “original” set indicates ground truth cell set. c, Energy distance of genes, mean of 25 cells per cell type, for reconstruction of scRNA-seq of unseen donors (N=3), calculated every 100 steps of the training on sets of 1, 5, 50 and 500 cells, for 90 treatments and 9 donors. In all runs, the network sees exactly 1000 cells in each forward pass, independent of cell set size. Latent shaping was not applied. d, same as c, but the minimal energy distance for each cell set size. e, the network was trained on the task of clustering sets of cells by treatment, trained on sets of 1, 5, 50 and 500 cells, for each run batches have the same amount of states to cluster per forward pass. The cosine similarity was measured for cell samples between treatments (higher better), or f, within treatment (lower better). g, Same as (f) but mean euclidean distance for cell samples between treatments (higher better), or h, within treatment (lower better). All measurements use the PARSE PBMCs dataset.\", \"page\": 6, \"index\": 1, \"width\": 504, \"height\": 627}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-03-14-711710-v2/fig-002.webp\", \"caption\": \"Fig. 5 | TRAILBLAZER stratifies individual patients' response to α-PD-1 treatment. a, Graphical abstract for virtual patient treatment, scRNA-seq data for an unseen group of patients is passed to the perturbation model to generate counterfactual dataset subsequently passed to multicellular classifier to measure efficacy of the treatment, pertinent to figures (b-e) for virtual treatment of breast cancer patients with anti-PD-1. b, ROC curves for predicting the response of naive breast cancer patients to α-PD-1 treatment. c, We trained a multicellular respondent/non-respondent classifier on a single-cell α-PD-1 dataset, labels reflect eventual clinical response to the anti-PD-1 treatment. For each patient, we predicted response probabilities for samples of 100 cells, repeated sampling 100 times, and showing underlying distribution as a violin plot. d, We have used TRAILBLAZER to apply α-PD-1 treatment in silico and repeated classification as in (c). e, As in (d) but after IL-10 treatment. f, Graphical abstract for virtual drug screening, initial and target multicellular states are used to calculate a phenotype vector compared to mechanism vectors with cosine similarity to rank treatments most likely moving in direction of desired health outcome. g, TRAILBLAZER’s top five zero-shot predictions for treatments augmenting ɑ-PD-1 response, derived from scRNA-seq biopsies of breast cancer patients treated with ɑ-PD-1. Success was assessed by literature review corroborating treatment efficacy. Predictions are shown for unseen patients. h, Same ranking task as in (g), performed with the CELLFLOW neural network on the identical data foundation, harmonized with TRAILBLAZER’s harmonizer module.\", \"page\": 10, \"index\": 2, \"width\": 982, \"height\": 733}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-03-14-711710-v2/fig-003.webp\", \"caption\": \"Fig. 3 | Application of latent space shaping using biological priors. a, To improve generalizability of TRAILBLAZER, the latent space of the network is shaped using a “Mechanism segmentation network” trained on a hypersphere manifold, and where healthy, unperturbed states are pushed towards the center and sick and perturbed states are put on the surface of the hypersphere. b, UMAP projection of the latent space for PARSE dataset’s 5 random treatments without latent shaping, and c, with latent shaping. d, same as b but view of 5 random donors without latent shaping, and e, with latent shaping. f, Average k-rank of treatment rediscovery for unseen donors based on cosine similarity of latent embeddings (lower better). g, Minimum energy distance for network without and with latent shaping calculated for each gene, averaged across 25 cells per cell type, for reconstruction of scRNA-seq of unseen donors (N=3), trained on sets of 500 cells. All measurements use the PARSE PBMCs scRNA-seq dataset.\", \"page\": 8, \"index\": 3, \"width\": 984, \"height\": 392}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-03-14-711710-v2/fig-004.webp\", \"caption\": \"Fig. 1 | TRAILBLAZER: Multicellular architecture for foundational models of biology. a, In multicellular organisms, sets of cells are working together to produce phenotypic presentations such as treatment response and disease progression. TRAILBLAZER operates on sets of cells to build uniform and traversable hypersphere latent representation of multicellular disease and treatment processes; it is coupled with multicellular classifiers to help with navigating the phenotypic space. b, Uniform disease-treatment phenotypic perturbation space can be applied to discover treatments by presenting initial and target patient phenotypes, or it can be used to identify patients phenotypes in response to treatments in virtual clinical trials, lastly multicellular architecture offers unbiased view of each cell importance to the process. c, TRAILBLAZER uses Induced Set Attention Blocks (ISAB)25 to efficiently capture relationships of large sets of cells’ biological variables such as scRNA-seq, and utilizes latent shaping with biological priors to improve generalizability by organizing latent space on a plan of hypersphere with healthy states in the center.\", \"page\": 4, \"index\": 4, \"width\": 984, \"height\": 789}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-03-14-711710-v2/fig-005.webp\", \"caption\": \"Fig. 6 | TRAILBLAZER’s cell attention can be used to aid granular analysis of diseases and treatments. a, The interpretability of the model predictions is afforded by multicellular phenotype classifier, trained to recognize desirable and undesirable cell states (e.g. responsiveness to treatment). It is capable of assessing cells’ state contribution to a disease/phenotype (cell importance), and it measures cells’ similarity to a desired state after treatment (responsiveness). b, The TRAILBLAZER phenotype classifier’s multicellular architecture outperforms the single-cell architectures of state-of-the-art models (Geneformer, scGPT, scVI). Models were trained on multilabel disease classification using patients’ scRNA-seq data, then evaluated on unseen patients. Performance was measured as F1 score of disease classification across training epochs. c, An example of TRAILBLAZER’s inferred importance of each cell type for the naive breast cancer patients, for a patient resistant to anti-PD-1 (left), and responsive (right). d, TRAILBLAZER AI predicted treatments improving anti-PD-1 patient responsiveness clustered by target cell populations. The average treatment responsiveness of each cell type is calculated across all patients (N=9). Treatments are clustered into four groups based on their predicted mechanism of action and are sorted from left to right based on the overall cosine similarity of cell states to positive patient outcomes. e, TRAILBLAZER AI models the contribution of each cell to anti-PD-1 patient responsiveness, an example of anti-PD-1/IL-15 effect on tumor micro-environment. A detailed view with single-cell resolution shows cells present before (1st column, top row) and after treatment (2nd column, top row), the importance of each cell to the state (middle row), and the treatment responsiveness of each cell (bottom row).\", \"page\": 12, \"index\": 5, \"width\": 979, \"height\": 618}]"
motivation: 现有单细胞模型忽略多细胞协同效应，难以在患者层面泛化并准确预测系统级干预反应。
method: 采用多细胞Transformer编码器结合超球形潜空间和计数感知生成解码器，实现细胞间上下文建模及通量预测。
result: TRAILBLAZER实现了零样本干预响应预测，可高精度评估免疫调节剂并保持单细胞分辨率。
conclusion: TRAILBLAZER为多细胞层面的预测与机制建模提供了新途径，有望成为治疗探索和生物系统预测的基础模型。
---

## 摘要
单细胞基础模型通过从数百万细胞状态谱中学习可迁移的表征，正在重塑生物学。这些模型支持注释、去噪、跨模态映射，并且越来越多地用于预测遗传或药理学扰动的响应。尽管取得了进展，但大多数方法将细胞视为独立的观测，忽略了决定组织行为的多细胞环境。基于汇总数据集训练的模型常常无法泛化至新的供体、实验室或干预条件，部分原因是其潜在空间缺乏用于组合与外推的结构。因此，强大的重建性能并不能保证系统级响应预测的准确性。

本研究所要解决的一般问题是，如何构建一个可扩展的模型，在保持单细胞分辨率的同时，预测多细胞、患者层面的干预响应，并实现对未观测条件的泛化。

我们表明，TRAILBLAZER——一个多细胞 transformer 编码器，结合显式构建的超球潜在空间和计数感知生成解码器——能够在患者分辨率层面上进行准确的零样本扰动响应预测与候选免疫调节剂排名。

与先前的单细胞或伪整体方法不同，TRAILBLAZER 将组织建模为协同系统，使用潜在 token 来汇总并重新分配全局上下文，同时保持与群体规模近似线性的扩展性。通过将潜在几何围绕共享的健康参照和校准的机制方向组织起来，该模型使向量运算在生物学上具有意义，并支持对未见作用剂的外推。这些结果共同确立了一个机制感知的多细胞响应模拟的实用框架，并为构建用于治疗发现的预测型基础模型指明了方向。

## Abstract
Single-cell foundation models are reshaping biology by learning transferable representations of cellular state from millions of profiles. These models support annotation, denoising, cross-modal mapping and, increasingly, prediction of responses to genetic or pharmacological perturbations. Despite this progress, most approaches treat cells as independent observations and ignore the multicellular context that governs tissue behavior. Models trained on aggregated datasets often fail to generalize to new donors, laboratories or interventions, in part because their latent spaces lack structure for composition and extrapolation. As a result, strong reconstruction performance does not guarantee accurate forecasting of system-level responses.

The general problem addressed here is how to construct a scalable model that predicts multicellular, patient-level responses to interventions while preserving single-cell resolution and enabling generalization beyond observed conditions.

Here we show that TRAILBLAZER, a multicellular transformer encoder coupled to an explicitly shaped hyperspherical latent space and a count-aware generative decoder, enables accurate zero-shot prediction of perturbation responses and ranking of candidate immunomodulators at patient resolution.

In contrast to prior single-cell or pseudo-bulk approaches, TRAILBLAZER models tissues as coordinated systems using latent tokens that summarize and redistribute global context while maintaining near-linear scaling with group size. By organizing latent geometry around shared healthy references and calibrated mechanistic directions, the model renders vector arithmetic biologically meaningful and supports extrapolation to unseen agents. Together, these results establish a practical framework for mechanism-aware simulation of multicellular responses and suggest a path toward predictive foundation models for therapeutic discovery.

---

## 论文详细总结（自动生成）

# TRAILBLAZER：生物学中生成式多细胞扰动模型 — 论文深入总结

---

## 1. 核心问题与整体含义

### 研究背景
- 当代生物学数据中，单细胞测序（scRNA-seq）提供了高分辨率的细胞状态信息，使得“单细胞基础模型”（single-cell foundation models）成为一种主流思路。
- 这些模型在表征学习、注释、跨模态映射等任务上表现优异，但普遍存在一个限制：**它们忽略了多细胞环境的整体协同机制**。
- 当前模型通常假设细胞是独立实体，导致难以在“系统级”生物过程（如组织响应或患者级干预反应）中泛化。
  
### 核心科学问题
> 如何在保持单细胞分辨率的同时，构建可扩展且具备外推能力的模型，以预测多细胞系统（甚至患者层面）对基因或药物扰动的真实反应？

TRAILBLAZER 的研究目标是解决这一泛化与多细胞建模瓶颈，将单细胞数据提升到**机制感知（mechanism-aware）**的多细胞层面预测。

---

## 2. 方法论：核心思想与技术细节

### 核心思想
- 将组织或样本视为一个“细胞集合”（cell set），通过多细胞 Transformer 的注意力机制建模细胞间的相互作用和全局上下文。
- 设计显式“超球形潜空间”（hyperspherical latent space），在该空间内健康状态居于中心，疾病和扰动状态分布于外层，实现语义化的潜空间结构。
- 结合**计数感知生成解码器（count-aware generative decoder）**，能够在不同细胞数目的样本间保持一致性。

### 技术架构
1. **编码器（Encoder）**：  
   - 使用 Induced Set Attention Blocks（ISAB）构建的多细胞 Transformer，针对输入的细胞集合，实现全体细胞间的上下文捕捉。  
   - 具有排列不变性（Permutation Invariance）和接近线性的复杂度。

2. **潜空间（Latent Space）**：  
   - 利用“机制分割网络（Mechanism Segmentation Network）”在超球面上对潜空间进行形塑。  
   - 健康状态 → 超球中心；疾病/扰动状态 → 超球表面。  
   - 支持生物学上有意义的向量运算（例如“健康状态 + 药物机制 = 治疗后状态”）。

3. **解码器（Decoder）**：  
   - 生成式模型，用于重建或预测细胞转录反应。  
   - 与计数感知模块配合，以维持在不同细胞集合规模下的稳定性。

4. **下游模块（Classifier / Harmonizer）**：  
   - 用于完成响应预测、候选药物排名和响应细胞类型解释等任务。
   - “Harmonizer”模块用于校准跨数据集分布差异，提高泛化能力。

---

## 3. 实验设计

### 数据与场景
- 数据集来源：
  - **PARSE PBMCs**：用于基准性能测试（例如能量距离、误差率、聚类一致性等）。
  - **乳腺癌患者 scRNA-seq 数据集**：用于患者层面 α-PD-1 治疗响应预测。
- 任务场景：
  - 零样本（zero-shot）预测未见治疗的患者响应。
  - 虚拟药物筛选与机制向量匹配。
  - 多细胞系统层面的响应生成与解释。

### 对比基线
- 与多种单细胞基础模型比较：
  - **Geneformer**
  - **scGPT**
  - **scVI**
- 基准指标包括：
  - F1 分数（疾病分类任务）
  - ROC 曲线（治疗响应预测）
  - 能量距离（重建误差）
  - 余弦相似度（机制向量一致性）

---

## 4. 资源与算力

- 论文中**未明确提及算力规格**（如 GPU 型号、数量、训练时长等）。
- 从描述推测模型支持较大规模的批次处理（每次前向传播使用约 1000 个细胞），暗示其可在典型的高性能 GPU 上运行（可能采用多卡或 A100 级别硬件）。

---

## 5. 实验数量与充分性

- 实验覆盖多个维度：
  - 不同细胞集合大小（1, 5, 50, 500 cells）。
  - 有无潜空间形塑的对比实验。
  - 零样本预测实验（跨患者、跨干预）。
  - 多细胞响应的聚类与可解释性测试。
- 总体而言，实验数量充足，涵盖了模型设计的关键因素。
- 对比方法合理、指标多样，评估过程较为客观；但**未说明交叉验证或统计显著性检验**，可能存在轻微偏差风险。

---

## 6. 主要结论与发现

- TRAILBLAZER 能够在患者分辨率层面准确预测干预响应，并具备显著的泛化能力。
- 模型在虚拟 α-PD-1 免疫治疗预测中表现出高准确性，可模拟药物反应并进行候选增强剂排名。
- 超球潜空间结构使得不同治疗、疾病状态的嵌入具有明确的方向性，促进机制感知学习。
- 多细胞注意力机制提高了解释性——模型可量化特定细胞类型对疾病或疗效的贡献。

---

## 7. 方法和实验的优点

- **机制感知潜空间设计**：在数学与生物意义上实现统一。
- **多细胞 Transformer 架构**：有效捕捉细胞间协作关系。
- **可解释性强**：可追踪到单细胞对整体状态的“重要度”和“响应性”。
- **扩展性佳**：复杂度近似线性，支持大样本规模。
- **跨患者泛化能力**：在未见供体和治疗条件下仍能保持稳定预测。

---

## 8. 不足与局限

- **算力要求和可复制性**：论文未披露训练细节，复现难度较高。
- **数据种类有限**：主要集中在血液和肿瘤免疫场景，其他组织类型的表现尚未验证。
- **统计验证不足**：缺乏误差置信区间或显著性评估。
- **模型复杂度高**：大型 Transformer + hypersphere 潜空间增加了调参和解释成本。
- **外推边界未明**：零样本推广对极端药物或未见病理机制的可靠性仍待验证。

---

（完）
