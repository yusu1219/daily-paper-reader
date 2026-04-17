---
title: A structure-informed deep learning framework for modeling TCR-peptide-HLA interactions
title_zh: 一种基于结构信息的深度学习框架，用于建模TCR-肽-HLA相互作用
authors: "Cao, K., Li, R., Strazar, M., Brown, E. M., Nguyen, P. N. U., Pust, M.-M., Park, J., Graham, D. B., Ashenberg, O., Uhler, C., Xavier, R."
date: 2026-04-11
pdf: "https://www.biorxiv.org/content/10.64898/2026.03.31.715361v2.full.pdf"
tags: ["query:gentcr"]
score: 9.0
evidence: 用于建模TCR-肽-HLA相互作用的深度学习框架，支持抗原特异性免疫分析
tldr: 本文提出了结构信息驱动的深度学习框架StriMap，用于准确建模T细胞受体（TCR）与肽-HLA的相互作用。通过融合物理化学、序列和结构特征，StriMap显著提升预测性能，并在强直性脊柱炎和炎症性肠病等自身免疫研究中验证了其应用潜力。
source: biorxiv
selection_source: fresh_fetch
figures_json: "[{\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-03-31-715361-v2/fig-001.webp\", \"caption\": \"Fig. 1: Overview of StriMap framework. (a) Biological context of T cell-mediated immune recognition. Cytotoxic T cells recognize target cells through the interaction between the T cell receptor (TCR) and peptide-HLA (pHLA) complexes presented on the surface of target cells. This tri-molecular interaction underlies antigen-specific immune surveillance and forms the biological basis of StriMap. (b) The architecture of the Sequence and Structure Feature Extractor (SSFE). Given a protein amino-acid sequence, SSFE integrates three complementary encoders: i) a physicochemical encoder that computes residue-level physicochemical features; ii) a sequence-based context encoder (e.g., ESM2 or ProtT5) that provides contextual sequence embeddings; and iii) a structural-derived geometric encoder (e.g., ESMFold) that generates 3D structural representations. Structural information is further processed through a multi-layer equivariant graph neural network (EGNN). All features are fused using gated cross-attention and layernormalization to produce a unified representation. (c) The bilinear attention network (BAN), which models pairwise interactions between two representations using learnable bilinear projections to generate multi-head attention maps. (d) Architecture of the peptide-HLA interaction predictor. Peptide and HLA sequences are independently encoded by SSFE and processed through transformer blocks, followed by gated cross-attention and BAN fusion. The fused representation is fed into a linear layer to produce an interaction score between 0-1. (e) Architecture of the TCR-peptide-HLA interaction predictor. TCR α/β chains, peptide, and HLA sequences are independently encoded by SSFE and then passed through a feature aggregator module that incorporates and leverages the embedding representations learned from\", \"page\": 25, \"index\": 1, \"width\": 970, \"height\": 657}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-03-31-715361-v2/fig-002.webp\", \"caption\": \"Fig. 3: StriMap supports two clinically relevant tasks for T cell-based immunotherapy.\", \"page\": 29, \"index\": 2, \"width\": 947, \"height\": 197}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-03-31-715361-v2/fig-003.webp\", \"caption\": \"Fig. 5: Experimental validation of AS-associated microbial mimicry peptides (a) Overview of discovery framework, in which StriMap prioritizes candidate disease-associated TCR-peptide-HLA interactions for experimental validation and iterative refinement. (b) Experimental workflow for validating interactions between the AS-associated TCR AS8.4 and candidate peptides. CD8⁺ Jurkat T cells were transduced to express the AS8.4 TCR and cocultured with HLA-B*27:05-expressing antigen-presenting cells (APCs) pulsed with candidate bacterial peptides. (c) Flow cytometry analysis of T cell activation following peptide stimulation. Activation was quantified by co-expression of CD69 (y-axis) and NFAT-driven ZsGreen reporter activity (xaxis). Three bacterial peptides induced robust T cell activation, comparable to the positive control, whereas negative and background controls showed minimal activation. Activated cells are enriched in the CD69⁺ZsGreen⁺ quadrant. (d) Metagenomic and metatranscriptomic profiling of bacterial peptide candidates across clinical cohorts. Heatmap shows the relative prevalence of peptide-associated features in healthy controls, infectious gastroenteritis, Crohn’s disease (CD), and ulcerative colitis (UC), following Z-score normalization. (e) Statistical comparison of peptide-associated features across diagnostic groups. A KruskalWallis test was performed across healthy, infectious gastroenteritis, UC, and CD cohorts. Features with significant group-level differences (p < 0.05) were further assessed using post hoc Dunn’s tests with multiple-comparison correction.\", \"page\": 32, \"index\": 3, \"width\": 969, \"height\": 605}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-03-31-715361-v2/fig-004.webp\", \"caption\": \"Fig. 2: StriMap achieves robust prediction of pHLA presentation and TCR-pHLA recognition. (a) Summary of pHLA presentation prediction performance across multiple benchmark datasets curated from independent prior studies. Methods are evaluated under in-distribution (ID), distribution-shifted (DS), and out-of-distribution (OOD) settings as defined by the original publications. Circle size indicates relative performance, and color denotes the corresponding dataset. Rankings are determined based on overall performance, with lighter color intensity indicating higher rankings within the dataset; white denotes the top-ranked method. (b) Comparison of StriMap and deepAntigen performance (AUPRC) across individual HLA alleles on the Que et al. dataset (ID). Each point represents one HLA allele, with color indicating HLA class and size denoting the number of peptide samples. The dashed diagonal line indicates equal performance. (c) True discovery rate (TDR) as a function of ranking threshold on the TESLA neoantigen benchmark. StriMap is compared with deepAntigen under the same evaluation protocol. The dashed line indicates the baseline discovery rate.\", \"page\": 27, \"index\": 4, \"width\": 877, \"height\": 785}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-03-31-715361-v2/fig-005.webp\", \"caption\": \"Fig. 4: Computational discovery of AS-associated bacterial mimicry peptides through cross-patient prediction. (a) AS-associated bacterial cohort and cross-patient few-shot prediction setup. We curated a literature-derived cohort of gut bacterial strains previously reported to be associated with ankylosing spondylitis (AS), spanning four major phyla: Bacillota, including Streptococcus spp., R. gnavus, etc.), Verrucomicrobiota (A. muciniphila), Bacteroidetes (P. copri, P. melaninogenica), and Proteobacteria (K. pneumoniae, E. coli, Parasutterella excrementihominis). To assess generalization to unseen patient TCRs, we implemented a crosspatient inference workflow in which TRBV9 TCR binding data from Patient 1 (AS3.1) and Patient 2 (AS4.1–AS4.4) were used as reference inputs to train the specificity model, and StriMap then predicted peptide-binding specificity for a query TRBV9 TCR from an independent Patient 3 (AS8.4), simulating a few-shot setting. (b) Large-scale in silico 9-mer peptide screening pipeline. The proteomes of the selected bacterial cohort, comprising 43,241 proteins, were retrieved and processed. A sliding window approach with a window size of k=9 and a stride of 1 amino acid was applied to generate a pool of approximately 13 million 9-mer peptides. The StriMap computational framework performs a dual-task prediction: Task 1 predicts the likelihood of HLA-B*27:05 presentation, and Task 2 predicts the recognition probability by specific TRBV9 TCRs (e.g., AS8.4). (c) Landscape of HLA-B27 high-affinity 9-mer peptides across the cohort. The bar chart illustrates the distribution and total count of predicted high-affinity 9-mer peptides for each bacterial strain. Strains such as K. pneumoniae and E. coli exhibit a high density of potential HLA-B27 binders, highlighting their significance in the molecular mimicry hypothesis. (d) Predicted reactivity scores for candidate bacterial peptides. Representative peptides from various phyla were ranked by their predicted reactivity scores against the target TCR. Highscoring candidates from Streptococcus spp. and A. muciniphila are compared against positive and negative controls, indicating potential cross-reactivity between bacterial antigens and ASassociated TCRs.\", \"page\": 31, \"index\": 5, \"width\": 953, \"height\": 493}]"
motivation: 当前对TCR与肽-HLA耦合识别的建模精度不足，限制了癌症和自身免疫研究的应用。
method: 提出了StriMap，将物理化学特征、序列上下文和结构信息整合以预测TCR-肽-HLA相互作用。
result: StriMap在预测性能和泛化能力上达到最新水平，并成功识别出导致强直性脊柱炎的候选分子模拟肽。
conclusion: StriMap为免疫疗法设计和自身免疫病抗原研究提供了通用化的预测框架。
---

## 摘要
T细胞受体（TCR）、肽和人类白细胞抗原（HLA）之间的相互作用是抗原特异性T细胞免疫的基础。尽管在肽-HLA呈递预测方面已有显著进展，但对耦合的TCR-肽-HLA识别的准确建模仍不完善，限制了其在癌症中TCR和新抗原优先级排序以及自身免疫中抗原识别等应用。本文提出StriMap，一个整合物理化学、序列上下文及结构特征于识别界面的统一框架，用于预测TCR-肽-HLA相互作用。StriMap实现了当前最先进的性能，具有改善的泛化能力，并可应用于癌症和自身免疫性疾病研究。以强直性脊柱炎（AS）为案例研究，我们筛选了来源于43,241种细菌蛋白的1,300万个肽，鉴定出可激活表达AS相关TCR的T细胞的候选分子模拟物，这些模拟物得到了实验证实。值得注意的是，一种验证度最高的肽在炎症性肠病（IBD）患者中富集，提示AS与IBD之间可能存在共享的微生物触发因素。总体而言，StriMap提供了一个具有普适性的框架，可用于合理设计免疫疗法并解析自身免疫的抗原驱动机制。

## Abstract
The interaction between T cell receptors (TCRs), peptides, and human leukocyte antigens (HLAs) underlies antigen-specific T cell immunity. Despite substantial advances in peptide- HLA presentation prediction, accurate modeling of coupled TCR-peptide-HLA recognition remains underdeveloped, limiting applications such as TCR and neoepitope prioritization in cancer and antigen identification in autoimmunity. Here we present StriMap, a unified framework for predicting TCR-peptide-HLA interactions by integrating physicochemical, sequence-context, and structural features at recognition interfaces. StriMap achieves state-of-the-art performance with improved generalizability and enables applications in both cancer and autoimmunity. As a case study in ankylosing spondylitis (AS), we screened 13 million peptides derived from 43,241 bacterial proteins and identified candidate molecular mimics that were experimentally validated to activate T cells expressing an AS-associated TCR. Notably, a top validated peptide was enriched in patients with inflammatory bowel disease (IBD), suggesting potential shared microbial triggers between AS and IBD. Overall, StriMap provides a generalizable framework for rational immunotherapy design and for dissecting antigenic drivers of autoimmunity.

---

## 论文详细总结（自动生成）

# 一种基于结构信息的深度学习框架，用于建模TCR-肽-HLA相互作用 — 中文总结

---

## 1. 研究背景与问题动机

- **核心问题**：T细胞受体（TCR）识别由人类白细胞抗原（HLA）呈递的抗原肽，是适应性免疫反应的关键过程。当前算法能够较好预测**肽-HLA结合**，但无法准确建模完整的**TCR–肽–HLA三分子相互作用**。  
- **动机与意义**：  
  - 在**癌症**中，TCR–肽–HLA识别的准确预测有助于优先选择新抗原（neoepitope）和TCR，用于个体化免疫治疗。  
  - 在**自身免疫病**中，理解异常TCR–抗原识别可揭示致病触发因素。  
- **现有限制**：传统模型往往仅基于序列信息，缺乏结构约束，导致在跨数据集或未知抗原下的**泛化能力弱**。

---

## 2. 方法论：StriMap 框架

### 核心思想
StriMap（**Structure-informed TRi-molecular Interaction Mapping**）旨在构建一个**统一的结构信息驱动深度学习框架**，同时预测：
1. 肽–HLA（pHLA）呈递；
2. TCR–pHLA识别。  
两者被视为一个**顺序耦合的生物过程**，而非两个独立任务。

### 技术架构
- **模块化结构**
  - **SSFE（Sequence and Structure Feature Extractor）**
    - 输入：肽、HLA、TCRα/β序列；
    - 特征通道：
      1. 物理化学特征（AAindex导出20维描述符）；
      2. 序列上下文特征（使用预训练语言模型 ESM2 或 ProtT5）；
      3. 三维几何特征（通过 ESMFold 预测结构 + SE(3)-等变图神经网络EGNN编码）。
  - **Bilinear Attention Network (BAN)**：建模分子间残基级双线性注意力，捕捉界面相互作用关系。
  - **层级架构**
    - 第一步：预测肽-HLA结合；
    - 第二步：在pHLA特征上再建模TCR识别，实现条件化的TCR评分。

### 训练策略
- **负样本设计**：
  - 动态负采样（DNS）：每轮重新生成随机负样本，扩大负样本空间；
  - 变异感知负采样（mutation-aware）：通过在肽或CDR3序列上引入1–3个突变生成“硬负样本”，提升模型区分细粒度差异的能力。  
- **损失函数**：采用焦点损失（Focal Loss）以应对类别不平衡问题。  
- **优化设置**：AdamW优化器、权重衰减、Dropout=0.1、梯度裁剪max norm=2、早停（patience 5–10）。

### 模型输出
- 肽-HLA结合打分（0–1）  
- TCR–pHLA相互作用打分（0–1）  
- 可通过Web平台（www.strimap.com）执行预测与模型微调。

---

## 3. 实验设计与Benchmark对比

### 数据来源与任务划分
- **任务1：肽–HLA呈递预测**  
  - 公共数据集：Albert et al. (2023), Chu et al. (2022), Que et al. (2025), TESLA (2020), CEDAR (2023)。  
- **任务2：TCR–pHLA识别预测**  
  - Benchmark：Zhang et al. (2018), Lu et al. (2026), IMMREP22/23挑 战赛集、Minervina et al. (2022)。  
- **分类标准**：
  - In-distribution (ID)、Distribution-shifted (DS)、Out-of-distribution (OOD)。

### 对比方法
- pHLA任务：NetMHCpan、deepAntigen、TransPHLA、MHCnuggets等。
- TCR任务：NetTCR系列、TCRGP、MixTCRpred、ERGO-LSTM、STAG、TAPIR 等。

### 评价指标
- AUROC、AUPRC、Top-K准召率、真发现率（TDR）。  
- 在癌症场景下采用TESLA和Melanoma数据进行**候选新抗原排名**验证。  
- 在自身免疫研究中进行**跨患者预测与实验验证**。

---

## 4. 算力与训练资源

- 明确说明：训练在 **NVIDIA A6000 GPU** 上进行；  
- 框架使用 **PyTorch 实现**；  
- 没有报告具体GPU数量与训练时长；  
- 每次训练上限为 100 epoch，使用5或10折交叉验证。

---

## 5. 实验数量与充分性

- **覆盖面广**：
  - pHLA呈递预测：≥3个独立Benchmark；
  - TCR识别预测：≥5个Benchmark；
  - 临床场景验证：癌症（TP53、黑色素瘤），自身免疫（强直性脊柱炎、IBD）。
- **消融实验**：
  - 去除结构模块；
  - 去除动态负采样；
  - 不同负采样策略（DNS、M1、M2）。  
- **评估充分**：交叉实验、外部分布测试（DS/OOD）、少样本任务（few-shot）均有覆盖。  
- **公平性**：保持与原始papers相同训练/测试划分；基线来自原文以避免复现偏差。

---

## 6. 主要结论与发现

1. **性能提升显著**：  
   - StriMap在所有pHLA和TCR–pHLA基准上均优于现有方法。  
   - 在更困难的分布漂移和零样本（OOD）场景下保持稳健。
2. **结构引导产生生物学合理嵌入**：  
   - 不同HLA等位基因在嵌入空间中形成可解释的聚类。  
3. **癌症免疫治疗应用**：  
   - 在TP53突变抗原识别和黑色素瘤疫苗新抗原筛选中显著提高Top-K真阳性率。  
4. **自身免疫应用**：  
   - 通过筛选43000余个细菌蛋白生成的1300万肽，发现3个可激活AS相关TCR的肽（来源于*Streptococcus*、*A. muciniphila*、*P. copri*）。  
   - 其中ARVMALMPF肽在IBD患者中富集，提示AS与IBD可能共享微生物抗原触发机制。  

---

## 7. 方法与设计亮点

- **耦合建模理念**：首次系统地将肽-HLA呈递与TCR识别建模为生物耦合层级过程。  
- **多模态结构整合**：结合序列语言模型与预测结构特征，实现结构推理而非仅依赖实验结构。  
- **动态与变异感知训练策略**：显著改善对稀疏数据的鲁棒性与判别性。  
- **可解释性增强**：嵌入与注意力权重揭示HLA特异位点及氨基酸敏感性。  
- **跨任务通用性**：在癌症、病毒感染、自身免疫中均可直接应用。  

---

## 8. 不足与局限

- **数据覆盖仍有限**：TCR–pHLA实验数据稀疏且偏向常见病毒抗原，零样本外推仍不稳定。  
- **结构动态未完全捕获**：模型结构基于静态ESMFold预测，未考虑构象变化。  
- **计算成本**：虽低于AlphaFold3等全结构模型，但大型语言模型+EGNN融合仍计算量大。  
- **应用范围**：目前仅覆盖HLA-I与CD8⁺细胞；HLA-II和CD4⁺识别尚未实现。  
- **缺乏明确时间-算力报告**：训练资源与可重复性信息略显不足。  

---

**（完）**
