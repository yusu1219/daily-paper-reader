---
title: A structure-informed deep learning framework for modeling TCR-peptide-HLA interactions
title_zh: 一种基于结构信息的深度学习框架用于建模TCR-肽-HLA相互作用
authors: "Cao, K., Li, R., Strazar, M., Brown, E. M., Nguyen, P. N. U., Pust, M.-M., Park, J., Graham, D. B., Ashenberg, O., Uhler, C., Xavier, R."
date: 2026-04-11
pdf: "https://www.biorxiv.org/content/10.64898/2026.03.31.715361v2.full.pdf"
tags: ["query:gentcr"]
score: 9.0
evidence: 用于 TCR-肽-HLA 相互作用建模的深度学习
tldr: 本文提出了StriMap框架，用于整合物理化学、序列和结构特征，以准确预测TCR-肽段-HLA相互作用。该方法在癌症和自身免疫研究中表现优异，并通过强直性脊柱炎案例验证了其应用潜力。
source: biorxiv
selection_source: fresh_fetch
figures_json: "[{\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-03-31-715361-v2/fig-001.webp\", \"caption\": \"Fig. 1: Overview of StriMap framework. (a) Biological context of T cell-mediated immune recognition. Cytotoxic T cells recognize target cells through the interaction between the T cell receptor (TCR) and peptide-HLA (pHLA) complexes presented on the surface of target cells. This tri-molecular interaction underlies antigen-specific immune surveillance and forms the biological basis of StriMap. (b) The architecture of the Sequence and Structure Feature Extractor (SSFE). Given a protein amino-acid sequence, SSFE integrates three complementary encoders: i) a physicochemical encoder that computes residue-level physicochemical features; ii) a sequence-based context encoder (e.g., ESM2 or ProtT5) that provides contextual sequence embeddings; and iii) a structural-derived geometric encoder (e.g., ESMFold) that generates 3D structural representations. Structural information is further processed through a multi-layer equivariant graph neural network (EGNN). All features are fused using gated cross-attention and layernormalization to produce a unified representation. (c) The bilinear attention network (BAN), which models pairwise interactions between two representations using learnable bilinear projections to generate multi-head attention maps. (d) Architecture of the peptide-HLA interaction predictor. Peptide and HLA sequences are independently encoded by SSFE and processed through transformer blocks, followed by gated cross-attention and BAN fusion. The fused representation is fed into a linear layer to produce an interaction score between 0-1. (e) Architecture of the TCR-peptide-HLA interaction predictor. TCR α/β chains, peptide, and HLA sequences are independently encoded by SSFE and then passed through a feature aggregator module that incorporates and leverages the embedding representations learned from\", \"page\": 25, \"index\": 1, \"width\": 970, \"height\": 657}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-03-31-715361-v2/fig-002.webp\", \"caption\": \"Fig. 3: StriMap supports two clinically relevant tasks for T cell-based immunotherapy.\", \"page\": 29, \"index\": 2, \"width\": 947, \"height\": 197}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-03-31-715361-v2/fig-003.webp\", \"caption\": \"Fig. 5: Experimental validation of AS-associated microbial mimicry peptides (a) Overview of discovery framework, in which StriMap prioritizes candidate disease-associated TCR-peptide-HLA interactions for experimental validation and iterative refinement. (b) Experimental workflow for validating interactions between the AS-associated TCR AS8.4 and candidate peptides. CD8⁺ Jurkat T cells were transduced to express the AS8.4 TCR and cocultured with HLA-B*27:05-expressing antigen-presenting cells (APCs) pulsed with candidate bacterial peptides. (c) Flow cytometry analysis of T cell activation following peptide stimulation. Activation was quantified by co-expression of CD69 (y-axis) and NFAT-driven ZsGreen reporter activity (xaxis). Three bacterial peptides induced robust T cell activation, comparable to the positive control, whereas negative and background controls showed minimal activation. Activated cells are enriched in the CD69⁺ZsGreen⁺ quadrant. (d) Metagenomic and metatranscriptomic profiling of bacterial peptide candidates across clinical cohorts. Heatmap shows the relative prevalence of peptide-associated features in healthy controls, infectious gastroenteritis, Crohn’s disease (CD), and ulcerative colitis (UC), following Z-score normalization. (e) Statistical comparison of peptide-associated features across diagnostic groups. A KruskalWallis test was performed across healthy, infectious gastroenteritis, UC, and CD cohorts. Features with significant group-level differences (p < 0.05) were further assessed using post hoc Dunn’s tests with multiple-comparison correction.\", \"page\": 32, \"index\": 3, \"width\": 969, \"height\": 605}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-03-31-715361-v2/fig-004.webp\", \"caption\": \"Fig. 2: StriMap achieves robust prediction of pHLA presentation and TCR-pHLA recognition. (a) Summary of pHLA presentation prediction performance across multiple benchmark datasets curated from independent prior studies. Methods are evaluated under in-distribution (ID), distribution-shifted (DS), and out-of-distribution (OOD) settings as defined by the original publications. Circle size indicates relative performance, and color denotes the corresponding dataset. Rankings are determined based on overall performance, with lighter color intensity indicating higher rankings within the dataset; white denotes the top-ranked method. (b) Comparison of StriMap and deepAntigen performance (AUPRC) across individual HLA alleles on the Que et al. dataset (ID). Each point represents one HLA allele, with color indicating HLA class and size denoting the number of peptide samples. The dashed diagonal line indicates equal performance. (c) True discovery rate (TDR) as a function of ranking threshold on the TESLA neoantigen benchmark. StriMap is compared with deepAntigen under the same evaluation protocol. The dashed line indicates the baseline discovery rate.\", \"page\": 27, \"index\": 4, \"width\": 877, \"height\": 785}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-03-31-715361-v2/fig-005.webp\", \"caption\": \"Fig. 4: Computational discovery of AS-associated bacterial mimicry peptides through cross-patient prediction. (a) AS-associated bacterial cohort and cross-patient few-shot prediction setup. We curated a literature-derived cohort of gut bacterial strains previously reported to be associated with ankylosing spondylitis (AS), spanning four major phyla: Bacillota, including Streptococcus spp., R. gnavus, etc.), Verrucomicrobiota (A. muciniphila), Bacteroidetes (P. copri, P. melaninogenica), and Proteobacteria (K. pneumoniae, E. coli, Parasutterella excrementihominis). To assess generalization to unseen patient TCRs, we implemented a crosspatient inference workflow in which TRBV9 TCR binding data from Patient 1 (AS3.1) and Patient 2 (AS4.1–AS4.4) were used as reference inputs to train the specificity model, and StriMap then predicted peptide-binding specificity for a query TRBV9 TCR from an independent Patient 3 (AS8.4), simulating a few-shot setting. (b) Large-scale in silico 9-mer peptide screening pipeline. The proteomes of the selected bacterial cohort, comprising 43,241 proteins, were retrieved and processed. A sliding window approach with a window size of k=9 and a stride of 1 amino acid was applied to generate a pool of approximately 13 million 9-mer peptides. The StriMap computational framework performs a dual-task prediction: Task 1 predicts the likelihood of HLA-B*27:05 presentation, and Task 2 predicts the recognition probability by specific TRBV9 TCRs (e.g., AS8.4). (c) Landscape of HLA-B27 high-affinity 9-mer peptides across the cohort. The bar chart illustrates the distribution and total count of predicted high-affinity 9-mer peptides for each bacterial strain. Strains such as K. pneumoniae and E. coli exhibit a high density of potential HLA-B27 binders, highlighting their significance in the molecular mimicry hypothesis. (d) Predicted reactivity scores for candidate bacterial peptides. Representative peptides from various phyla were ranked by their predicted reactivity scores against the target TCR. Highscoring candidates from Streptococcus spp. and A. muciniphila are compared against positive and negative controls, indicating potential cross-reactivity between bacterial antigens and ASassociated TCRs.\", \"page\": 31, \"index\": 5, \"width\": 953, \"height\": 493}]"
motivation: 现有模型在联合预测TCR与肽-HLA识别方面准确性不足，限制了癌症和自身免疫研究的应用。
method: 研究通过整合结构、序列和理化特征构建统一的深度学习模型StriMap来预测三者相互作用。
result: StriMap在预测TCR-肽段-HLA相互作用上达到了最先进的性能，并在癌症和自身免疫研究中具备良好的泛化能力。
conclusion: StriMap为设计理性免疫疗法和解析自身免疫疾病的抗原驱动机制提供了通用的计算工具。
---

## 摘要
T细胞受体（TCR）、肽段和人类白细胞抗原（HLA）之间的相互作用是抗原特异性T细胞免疫的基础。尽管肽-HLA呈递预测已取得显著进展，但对耦合的TCR-肽-HLA识别的精确建模仍不充分，从而限制了其在癌症中的TCR与新生抗原优先级排序以及在自身免疫中抗原鉴定等应用。在此，我们提出了StriMap，这是一种统一框架，通过整合物理化学特征、序列上下文信息及识别界面的结构特征，来预测TCR-肽-HLA相互作用。StriMap在通用性方面取得了最新的性能突破，并支持癌症与自身免疫两方面的应用。作为强直性脊柱炎（AS）的案例研究，我们筛选了来源于43,241种细菌蛋白的1,300万个肽段，鉴定出了能够激活表达AS相关TCR的T细胞的候选分子模拟物，并获得了实验验证。值得注意的是，其中一种验证通过的高得分肽段在炎症性肠病（IBD）患者中富集，提示AS与IBD之间可能存在共同的微生物触发因素。总体而言，StriMap提供了一个具有广泛适用性的框架，可用于理性设计免疫疗法以及剖析自身免疫的抗原驱动机制。

## Abstract
The interaction between T cell receptors (TCRs), peptides, and human leukocyte antigens (HLAs) underlies antigen-specific T cell immunity. Despite substantial advances in peptide- HLA presentation prediction, accurate modeling of coupled TCR-peptide-HLA recognition remains underdeveloped, limiting applications such as TCR and neoepitope prioritization in cancer and antigen identification in autoimmunity. Here we present StriMap, a unified framework for predicting TCR-peptide-HLA interactions by integrating physicochemical, sequence-context, and structural features at recognition interfaces. StriMap achieves state-of-the-art performance with improved generalizability and enables applications in both cancer and autoimmunity. As a case study in ankylosing spondylitis (AS), we screened 13 million peptides derived from 43,241 bacterial proteins and identified candidate molecular mimics that were experimentally validated to activate T cells expressing an AS-associated TCR. Notably, a top validated peptide was enriched in patients with inflammatory bowel disease (IBD), suggesting potential shared microbial triggers between AS and IBD. Overall, StriMap provides a generalizable framework for rational immunotherapy design and for dissecting antigenic drivers of autoimmunity.

---

## 论文详细总结（自动生成）

# 一种基于结构信息的深度学习框架用于建模 TCR-肽-HLA 相互作用 —— 综合总结

---

## 一、研究动机与核心问题

- **背景**：T 细胞免疫反应依赖于 T 细胞受体（TCR）识别由人类白细胞抗原（HLA）分子呈递的肽段复合物（pHLA）。准确建模这一三分子相互作用（TCR–肽–HLA）对于理解免疫识别、设计癌症免疫疗法以及解析自身免疫性疾病具有重大意义。  
- **问题现状**：  
  - 现有的计算方法主要聚焦于预测**肽–HLA 呈递**或**TCR–pHLA 结合**的子任务。  
  - 缺乏一个**统一、结构感知**的模型，能够将肽呈递与 TCR 识别作为一个**耦合的生物过程**进行建模。  
  - 由于实验数据稀缺且偏倚严重，模型在跨数据集、跨疾病的情境下泛化性较差。  
- **研究目标**：提出一个能够融合结构、序列及物理化学特征的通用框架，以提高预测准确度并拓展其在肿瘤和自身免疫领域的实用性。

---

## 二、方法论：StriMap 框架

### 1. 核心思想
StriMap（**Structure-informed TRi-molecular Interaction Mapping**）是一种**统一的深度学习框架**，通过耦合建模肽–HLA 呈递与 TCR 识别过程，捕捉免疫识别的结构与序列特征，从而实现高精度预测与跨场景泛化。

### 2. 模型结构
由两大模块组成：
- **（1）肽–HLA 预测器（pHLA predictor）**  
  负责学习肽与 HLA 分子的结合特征。
- **（2）TCR–pHLA 预测器**  
  在前者的基础上进一步学习 TCR 与 pHLA 的耦合识别。

二者共享底层表征模块，即：

#### Sequence and Structure Feature Extractor（SSFE）
整合三类特征：
1. **理化属性特征**（AAindex 提取 20 维残基特征，如疏水性、电荷、极性等）；  
2. **序列上下文编码**（基于蛋白预训练语言模型，如 ESM2、ProtT5）；  
3. **结构几何特征**（通过 ESMFold 预测的三维结构经 EGNN 处理，以捕捉原子几何关系）。

融合机制采用**门控交叉注意力（gated cross-attention）**实现多模态信息整合。

#### 接口建模：双线性注意力网络（Bilinear Attention Network，BAN）
- 通过双线性兼容函数建模残基间交互关系；
- 显式计算二维注意矩阵以捕获多分子接触依赖；
- 最终输出交互向量表示用于预测得分（0–1）。

#### 训练策略与优化
- **负样本构建**：
  - 动态随机重采样（Dynamic Negative Sampling, DNS）；
  - 突变感知负样本（Mutation-aware Sampling），在肿瘤新抗原场景中生成轻微突变的肽或 CDR3 序列。  
- **损失函数**：焦点损失（Focal Loss）以应对类别不平衡；
- **优化器**：AdamW，学习率、正则化与剪枝参数均已明示；
- **训练框架**：PyTorch。

---

## 三、实验设计

### 1. 数据来源与场景
- **pHLA 建模任务**：采用来自多个独立研究的数据集（如 Que et al., Chu et al., Albert et al.），覆盖多种 HLA 等位基因。
- **TCR–pHLA 预测任务**：
  - 取自常用基准集合 IMMREP22、IMMREP23、Lu et al.、Zhang et al.、Minervina et al. 等；
  - 涵盖新冠病毒（SARS-CoV-2）免疫应答、癌症抗原及自身免疫相关数据。
- **实际应用场景**：
  1. **癌症研究**：TP53 突变肽的新抗原和其特异性 TCR 排序；黑色素瘤个体化疫苗设计（Blass et al., 2025 数据）。  
  2. **自身免疫研究**：强直性脊柱炎（AS）中 HLA-B*27:05 与 TRBV9 模体相关肠道菌群肽段筛选（约 1300 万肽段）。

### 2. 对比基线
包括传统与深度学习方法：  
NetMHCpan、deepAntigen、BigMHC、MHCnuggets、NetTCR、MixTCRpred、ERGO、TAPIR 等。  

### 3. 评测指标
- AUROC、AUPRC、True Discovery Rate（TDR）；
- 在三种分布设定下评估：**ID（同分布） / DS（跨数据集） / OOD（未知抗原）**；
- 还包括**可视化嵌入分析**（UMAP 群聚）、**注意力可解释分析**及**突变敏感性实验**。

---

## 四、资源与算力

- 明确提到：
  - 使用 **NVIDIA A6000 GPU**；
  - 框架：**PyTorch**；
  - 训练批量 256；
  - 采用 5/10 折交叉验证与早停机制。
- 文中未说明具体 GPU 数量、训练时长及计算消耗。

---

## 五、实验规模与充分性

- 共涵盖 **两大类任务（pHLA预测、TCR–pHLA预测）** 和 **两种疾病场景（癌症、自身免疫）**；  
- 使用 **多个公开基准数据集（>10 个）**；
- 消融实验包括：
  - 去除结构模块（w/o-Stru）；  
  - 去除动态负采样（w/o-DNS）；  
  - 加入突变负样本的不同策略（M1、M2）。
- 另进行**少样本迁移学习（few-shot）**评估，在患者级别预测中验证模型鲁棒性。  
- 实验设计系统且客观，评测协议与基线论文一致，公认结果具有可再现性与公平性。

---

## 六、主要发现与结论

- **性能突破**：在所有 pHLA 与 TCR–pHLA 基准中均取得**SOTA**表现，尤其在跨分布与零样本测试中具备更高稳健性。  
- **特征可解释性增强**：模型嵌入能自动聚类出 HLA 亚型间的结构差异；注意力权重揭示关键结合位点。  
- **临床应用成果**：
  - 在癌症中，准确区分突变与野生型序列带来的免疫差异，提升新抗原与 TCR 的优先排序；
  - 在自身免疫中，发现并实验证实多条来源于**Streptococcus**与**Akkermansia**属的拟态肽能激活 AS 相关 TCR；
  - 一种关键肽（ARVMALMPF）在 **炎症性肠病（IBD）** 患者中富集，提示潜在共通微生物触发因素。

---

## 七、创新点与优点

- **统一建模理念**：首次将 pHLA 呈递与 TCR 识别整合为一个层级耦合的整体过程。  
- **结构感知与多模态融合**：结合 ESMFold + EGNN，无需实验结构即可捕捉几何信息。  
- **动态与突变感知负采样**：增强模型区分能力与现实生物意义。  
- **跨领域应用**：一套模型兼顾癌症精准免疫与自身免疫机制探索。  
- **可解释性高、可视化直观**：通过注意力与嵌入投影，揭示不同 HLA 亚型或 TCR 的特异识别特征。  
- **开放资源友好**：代码、模型与网站（www.strimap.com）均公开可用。

---

## 八、局限性与不足

- **数据稀缺与偏倚**：
  - TCR–pHLA 数据显著不平衡，特定抗原占主导；
  - 可能导致零样本泛化受限。  
- **动态构象缺失**：
  - 静态结构预测无法捕捉分子结合的动态变化。  
- **硬件代价与可扩展性**：
  - 尽管比 AlphaFold3 轻量，但在蛋白组级筛选中计算成本仍高。  
- **应用范围**：
  - 目前限制于 **HLA-I 与 CD8⁺ T 细胞**，未覆盖 HLA-II 与辅助性 T 细胞反应。  
- **评估覆盖性有限**：
  - 一些外部分布（e.g. IMMREP23 OOD）中仍存在性能波动；
  - 临床验证数量有限（10 条候选肽中 3 条成功验证）。

---

**（完）**
