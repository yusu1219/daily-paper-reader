---
title: A structure-informed deep learning framework for modeling TCR-peptide-HLA interactions
title_zh: 一种基于结构信息的深度学习框架，用于建模TCR-肽-HLA相互作用
authors: "Cao, K., Li, R., Strazar, M., Brown, E. M., Nguyen, P. N. U., Pust, M.-M., Park, J., Graham, D. B., Ashenberg, O., Uhler, C., Xavier, R."
date: 2026-04-11
pdf: "https://www.biorxiv.org/content/10.64898/2026.03.31.715361v2.full.pdf"
tags: ["query:gentcr"]
score: 9.0
evidence: 使用深度学习模拟 TCR-肽-HLA 相互作用
tldr: 本研究提出了结构信息驱动的深度学习框架StriMap，用于精准建模TCR-肽-HLA相互作用。该方法综合物理化学、序列与结构特征，实现了更高准确性，并在强直性脊柱炎研究中识别出可激活特定TCR的细菌肽，揭示了其与炎症性肠病可能存在共同免疫触发机制。
source: biorxiv
selection_source: fresh_fetch
figures_json: "[{\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-03-31-715361-v2/fig-001.webp\", \"caption\": \"Fig. 1: Overview of StriMap framework. (a) Biological context of T cell-mediated immune recognition. Cytotoxic T cells recognize target cells through the interaction between the T cell receptor (TCR) and peptide-HLA (pHLA) complexes presented on the surface of target cells. This tri-molecular interaction underlies antigen-specific immune surveillance and forms the biological basis of StriMap. (b) The architecture of the Sequence and Structure Feature Extractor (SSFE). Given a protein amino-acid sequence, SSFE integrates three complementary encoders: i) a physicochemical encoder that computes residue-level physicochemical features; ii) a sequence-based context encoder (e.g., ESM2 or ProtT5) that provides contextual sequence embeddings; and iii) a structural-derived geometric encoder (e.g., ESMFold) that generates 3D structural representations. Structural information is further processed through a multi-layer equivariant graph neural network (EGNN). All features are fused using gated cross-attention and layernormalization to produce a unified representation. (c) The bilinear attention network (BAN), which models pairwise interactions between two representations using learnable bilinear projections to generate multi-head attention maps. (d) Architecture of the peptide-HLA interaction predictor. Peptide and HLA sequences are independently encoded by SSFE and processed through transformer blocks, followed by gated cross-attention and BAN fusion. The fused representation is fed into a linear layer to produce an interaction score between 0-1. (e) Architecture of the TCR-peptide-HLA interaction predictor. TCR α/β chains, peptide, and HLA sequences are independently encoded by SSFE and then passed through a feature aggregator module that incorporates and leverages the embedding representations learned from\", \"page\": 25, \"index\": 1, \"width\": 970, \"height\": 657}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-03-31-715361-v2/fig-002.webp\", \"caption\": \"Fig. 3: StriMap supports two clinically relevant tasks for T cell-based immunotherapy.\", \"page\": 29, \"index\": 2, \"width\": 947, \"height\": 197}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-03-31-715361-v2/fig-003.webp\", \"caption\": \"Fig. 5: Experimental validation of AS-associated microbial mimicry peptides (a) Overview of discovery framework, in which StriMap prioritizes candidate disease-associated TCR-peptide-HLA interactions for experimental validation and iterative refinement. (b) Experimental workflow for validating interactions between the AS-associated TCR AS8.4 and candidate peptides. CD8⁺ Jurkat T cells were transduced to express the AS8.4 TCR and cocultured with HLA-B*27:05-expressing antigen-presenting cells (APCs) pulsed with candidate bacterial peptides. (c) Flow cytometry analysis of T cell activation following peptide stimulation. Activation was quantified by co-expression of CD69 (y-axis) and NFAT-driven ZsGreen reporter activity (xaxis). Three bacterial peptides induced robust T cell activation, comparable to the positive control, whereas negative and background controls showed minimal activation. Activated cells are enriched in the CD69⁺ZsGreen⁺ quadrant. (d) Metagenomic and metatranscriptomic profiling of bacterial peptide candidates across clinical cohorts. Heatmap shows the relative prevalence of peptide-associated features in healthy controls, infectious gastroenteritis, Crohn’s disease (CD), and ulcerative colitis (UC), following Z-score normalization. (e) Statistical comparison of peptide-associated features across diagnostic groups. A KruskalWallis test was performed across healthy, infectious gastroenteritis, UC, and CD cohorts. Features with significant group-level differences (p < 0.05) were further assessed using post hoc Dunn’s tests with multiple-comparison correction.\", \"page\": 32, \"index\": 3, \"width\": 969, \"height\": 605}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-03-31-715361-v2/fig-004.webp\", \"caption\": \"Fig. 2: StriMap achieves robust prediction of pHLA presentation and TCR-pHLA recognition. (a) Summary of pHLA presentation prediction performance across multiple benchmark datasets curated from independent prior studies. Methods are evaluated under in-distribution (ID), distribution-shifted (DS), and out-of-distribution (OOD) settings as defined by the original publications. Circle size indicates relative performance, and color denotes the corresponding dataset. Rankings are determined based on overall performance, with lighter color intensity indicating higher rankings within the dataset; white denotes the top-ranked method. (b) Comparison of StriMap and deepAntigen performance (AUPRC) across individual HLA alleles on the Que et al. dataset (ID). Each point represents one HLA allele, with color indicating HLA class and size denoting the number of peptide samples. The dashed diagonal line indicates equal performance. (c) True discovery rate (TDR) as a function of ranking threshold on the TESLA neoantigen benchmark. StriMap is compared with deepAntigen under the same evaluation protocol. The dashed line indicates the baseline discovery rate.\", \"page\": 27, \"index\": 4, \"width\": 877, \"height\": 785}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-03-31-715361-v2/fig-005.webp\", \"caption\": \"Fig. 4: Computational discovery of AS-associated bacterial mimicry peptides through cross-patient prediction. (a) AS-associated bacterial cohort and cross-patient few-shot prediction setup. We curated a literature-derived cohort of gut bacterial strains previously reported to be associated with ankylosing spondylitis (AS), spanning four major phyla: Bacillota, including Streptococcus spp., R. gnavus, etc.), Verrucomicrobiota (A. muciniphila), Bacteroidetes (P. copri, P. melaninogenica), and Proteobacteria (K. pneumoniae, E. coli, Parasutterella excrementihominis). To assess generalization to unseen patient TCRs, we implemented a crosspatient inference workflow in which TRBV9 TCR binding data from Patient 1 (AS3.1) and Patient 2 (AS4.1–AS4.4) were used as reference inputs to train the specificity model, and StriMap then predicted peptide-binding specificity for a query TRBV9 TCR from an independent Patient 3 (AS8.4), simulating a few-shot setting. (b) Large-scale in silico 9-mer peptide screening pipeline. The proteomes of the selected bacterial cohort, comprising 43,241 proteins, were retrieved and processed. A sliding window approach with a window size of k=9 and a stride of 1 amino acid was applied to generate a pool of approximately 13 million 9-mer peptides. The StriMap computational framework performs a dual-task prediction: Task 1 predicts the likelihood of HLA-B*27:05 presentation, and Task 2 predicts the recognition probability by specific TRBV9 TCRs (e.g., AS8.4). (c) Landscape of HLA-B27 high-affinity 9-mer peptides across the cohort. The bar chart illustrates the distribution and total count of predicted high-affinity 9-mer peptides for each bacterial strain. Strains such as K. pneumoniae and E. coli exhibit a high density of potential HLA-B27 binders, highlighting their significance in the molecular mimicry hypothesis. (d) Predicted reactivity scores for candidate bacterial peptides. Representative peptides from various phyla were ranked by their predicted reactivity scores against the target TCR. Highscoring candidates from Streptococcus spp. and A. muciniphila are compared against positive and negative controls, indicating potential cross-reactivity between bacterial antigens and ASassociated TCRs.\", \"page\": 31, \"index\": 5, \"width\": 953, \"height\": 493}]"
motivation: 现有模型对TCR-肽-HLA识别的准确建模仍不足，限制了癌症免疫治疗和自身免疫研究的应用。
method: 研究提出StriMap框架，整合物理化学、序列上下文与结构特征预测TCR-肽-HLA相互作用。
result: StriMap在预测性能和泛化性上达到最先进水平，并在强直性脊柱炎研究中验证了细菌肽的潜在自身免疫触发作用。
conclusion: StriMap为深入理解和预测TCR-肽-HLA相互作用提供了通用框架，促进了免疫治疗设计和自身免疫研究。
---

## 摘要
T细胞受体（TCR）、肽段和人类白细胞抗原（HLA）之间的相互作用是抗原特异性T细胞免疫的基础。尽管肽-HLA呈递预测已有显著进展，但对耦合的TCR-肽-HLA识别进行精确建模仍未充分发展，这限制了其在癌症中TCR与新抗原优先级排序，以及在自身免疫性疾病中抗原识别等应用。在此，我们提出了StriMap，这是一种用于预测TCR-肽-HLA相互作用的统一框架，通过整合识别界面的物理化学特征、序列上下文以及结构特征。StriMap在性能和泛化能力上均达到了当前最优水平，并支持其在癌症和自身免疫领域的多种应用。以强直性脊柱炎（AS）为案例研究，我们筛选了源自43,241种细菌蛋白的1,300万个肽段，并鉴定出候选的分子模拟物，这些模拟物被实验证实可激活表达与AS相关TCR的T细胞。值得注意的是，一个经过验证的高评分肽段在炎症性肠病（IBD）患者中富集，提示AS与IBD之间可能存在共同的微生物诱因。总体而言，StriMap为理性免疫治疗设计及解析自身免疫的抗原驱动机制提供了一个具有广泛适用性的通用框架。

## Abstract
The interaction between T cell receptors (TCRs), peptides, and human leukocyte antigens (HLAs) underlies antigen-specific T cell immunity. Despite substantial advances in peptide- HLA presentation prediction, accurate modeling of coupled TCR-peptide-HLA recognition remains underdeveloped, limiting applications such as TCR and neoepitope prioritization in cancer and antigen identification in autoimmunity. Here we present StriMap, a unified framework for predicting TCR-peptide-HLA interactions by integrating physicochemical, sequence-context, and structural features at recognition interfaces. StriMap achieves state-of-the-art performance with improved generalizability and enables applications in both cancer and autoimmunity. As a case study in ankylosing spondylitis (AS), we screened 13 million peptides derived from 43,241 bacterial proteins and identified candidate molecular mimics that were experimentally validated to activate T cells expressing an AS-associated TCR. Notably, a top validated peptide was enriched in patients with inflammatory bowel disease (IBD), suggesting potential shared microbial triggers between AS and IBD. Overall, StriMap provides a generalizable framework for rational immunotherapy design and for dissecting antigenic drivers of autoimmunity.

---

## 论文详细总结（自动生成）

# 一种基于结构信息的深度学习框架，用于建模 TCR-肽-HLA 相互作用 —— 中文详细总结

---

## 1. 核心问题与研究背景

- **研究动机**  
  T 细胞免疫反应依赖于 **T 细胞受体（TCR）** 对经 **人类白细胞抗原（HLA）** 呈递的 **抗原肽（peptide）** 的特异识别。这一三元复合体系（TCR–peptide–HLA）是适应性免疫识别的核心。  
  尽管在 *peptide–HLA* 呈递预测方面已有显著进步（如 NetMHCpan 系列），但对 **耦合的 TCR–peptide–HLA 识别** 的建模至今仍存在以下挑战：
  - 数据稀缺与不平衡；
  - 结构多样性难以捕获；
  - 主流方法往往将 “HLA 呈递” 与 “TCR 识别” 独立建模，忽略了层级依赖关系；
  - 结果泛化性较差，难以推广到新抗原或罕见 HLA 背景。

- **研究目的**  
  作者旨在构建一个统一框架，利用 **深度学习与结构信息融合** 的方法，**耦合模拟** 从肽呈递到 TCR 识别的整个免疫识别过程，从而提升预测准确率与跨任务泛化能力。

---

## 2. 方法论：StriMap 框架

### 2.1 核心思想
- **StriMap（Structure-informed TRi-molecular Interaction Mapping）**  
  是一个统一的端到端深度学习系统，首次同时建模：
  1. **peptide–HLA 呈递**；
  2. **TCR–pHLA 识别**。  
  其基本结构按生物层级顺序串联，保证预测的生物一致性。

### 2.2 模型架构要点
1. **多模态特征编码器（SSFE）**：  
   同时提取三类互补特征：
   - **物理化学特征**（20维AAindex向量，包括疏水性、电荷、体积、极性等）；
   - **序列上下文特征**（蛋白语言模型如 ESM2、ProtT5 提取的隐含嵌入）；
   - **结构几何特征**（由 ESMFold 预测三维结构，经 SE(3)-等变图神经网络 EGNN 提取空间嵌入）。

2. **融合机制**  
   - 采用 **门控交叉注意力（gated cross-attention）** 融合不同模态；
   - **双线性注意力网络（BAN）** 建模肽–HLA、TCR–pHLA 的残基级相互作用；
   - 整体形成 “从呈递到识别的层级管线”。

3. **负样本策略**  
   - **动态负采样（DNS）**：每个 epoch 改变随机负样本，扩展负样本空间；
   - **突变感知采样（mutation-aware negatives）**：随机突变肽或 TCR 的 1–3 个残基，构造近似但非真实结合体，以增强区分能力。

4. **训练与优化**
   - **损失函数**：Focal Loss（应对正负样本不平衡）；
   - **优化器**：AdamW；
   - **dropout=0.1，梯度裁剪 2.0，最大 epoch=100**；
   - **早停策略 (patience=5/10) 与 5/10 折交叉验证**。

5. **分层模块**
   - **pHLA 模块**：预测肽–HLA 亲和性；
   - **TCR–pHLA 模块**：以第一模块的嵌入作为条件输入，评估 TCR 特异性结合强度。

---

## 3. 实验设计与数据集

### 3.1 数据来源与任务设置
- **任务一：肽–HLA 呈递预测**
  - 使用多个公开 benchmark（如 Chu et al. 2022；Que et al. 2025；Albert et al. 2023）；
  - 区分 **in-distribution (ID)、distribution-shifted (DS)** 与 **out-of-distribution (OOD)** 测试环境；
  - 与 **NetMHCpan、deepAntigen、BigMHC、MixMHCpred** 等模型对比。

- **任务二：TCR–pHLA 识别预测**
  - 使用 **IMMREP22、IMMREP23、Zhang et al.、Lu et al.、Minervina et al.** 等数据库；
  - 生成负样本采用 shuffle 与突变策略；
  - 对比模型包括 **NetTCR、MixTCRpred、ERGO、TCRGP、TCRex、STAPLER** 等。

- **场景三：癌症免疫治疗**
  - TP53 突变位点及其新抗原；
  - melanoma 患者（106 个突变肽、配对 TCR 库）；
  - 与 TAPIR、NetTCR、NetMHCpan-4.2 (EL/BA) 对比。

- **场景四：自身免疫—强直性脊柱炎（AS）**
  - 聚焦 HLA-B*27:05 与 TRBV9 TCR；
  - 从 16 种与 AS 相关的细菌株（43,241 蛋白）生成 **1300 万肽段**；
  - 筛选高亲和性肽并预测可激活 AS 相关 TCR 的候选分子模拟物；
  - 后续进行 **体外实验验证** 与 **在炎症性肠病（IBD）样本中的富集分析**。

---

## 4. 资源与算力

- 训练在 **NVIDIA A6000 GPU** 上完成，基于 **PyTorch 框架**；
- 未明确说明 GPU 数量与训练总时长；
- 提供了公开 web 工具与代码仓库：
  - [StriMap Tools GitHub](https://github.com/uhlerlab/strimap-tools)  
  - [www.strimap.com](http://www.strimap.com)（含预测与微调功能）。

---

## 5. 实验数量与充分性

- **Benchmark 实验**：至少 6 个公开数据集、覆盖 3 种分布级别（ID/DS/OOD）；  
- **消融实验**：移除结构模块或 DNS 机制，AUROC/AUPRC 均下降；  
- **病例评测**：癌症免疫和自身免疫各有一完整研究场景；  
- **体外验证实验**：测试 10 条候选肽，与阳性 / 阴性对照对比。  
→ 实验覆盖广泛、指标完备（AUROC、AUPRC、TDR、Recall–Rank），总体较为充分，并遵循公平基准对比。

---

## 6. 主要结论与发现

- **综合性能最优**：  
  在肽–HLA 和 TCR–pHLA 两项任务的所有基准测试中，StriMap 均超越现有方法。

- **结构信息显著增强泛化**：  
  结构模块的加入显著提升 OOD 表现，捕获了 HLA 等位基因间的微差异。

- **应用拓展**：
  - 在 **癌症场景**：能准确排序 TP53 突变来源的抗原及相应 TCR；
  - 在 **AS 场景**：筛出 3 条细菌肽被实验证实能激活疾病相关 TCR；
  - 其中 Streptococcus 源肽 **ARVMALMPF** 在 IBD 样本中富集，提示 AS/IBD 可能共享免疫触发因子。

- **框架可推广性强**：同时适用于疫苗设计、TCR 筛选、抗原发掘等多任务。

---

## 7. 方法优势与创新点

- **层级耦合架构**：首次将肽呈递与 TCR 识别视为连续生物过程；
- **结构增强特征**：在无晶体结构的情况下利用预测结构（ESMFold + EGNN）；
- **双线性注意力机制**：更细粒度地建模残基相互作用；
- **动态 / 突变采样策略**：有效缓解负样本稀缺和过拟合；
- **通用性与可用性**：提供开源代码与在线工具，支持少样本微调；
- **跨任务验证**：在癌症与自身免疫两类疾病中均获得实验支持。

---

## 8. 不足与局限

- **零样本泛化仍受限**：完全未见过的肽–TCR 组合泛化性仍较低；
- **结构动态性未考虑**：静态结构特征无法反映构象变动；
- **主要针对 HLA-I / CD8⁺ 体系**，尚未覆盖 HLA-II / CD4⁺ 背景；
- **计算开销较大**：虽未量化，但多级结构模块和语言模型计算需求高；
- **OOD 基准样本有限**：如 IMMREP23 仅含 3 个未见表位，统计代表性受限；
- **实验验证仍有限**：体外验证规模较小，临床样本外推需要更多独立数据。

---

**（完）**
