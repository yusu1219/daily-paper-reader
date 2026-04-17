---
title: "IMMREP25: Unseen Peptides"
title_zh: IMMREP25：未知肽
authors: "Richardson, E., Aarts, Y. J. M., Altin, J. A., Baakman, C. A. B., Bradley, P., Chen, B., Clifford, J., Dhar, M., Diepenbroek, D., Fast, E., Gowthaman, R., He, J., Karnaukhov, V., Marzella, D. F., Meysman, P., Nielsen, M., Nilsson, J. B., Deleuran, S. N., Parizi, F. M., Pelissier, A., Pierce, B. G., Rodriguez Martinez, M., Roran A R, D., Saravanakumar, S., Shao, Y., Smit, N., Van Houcke, M., Visani, G. M., Wan, Y.-T. R., Wang, X., Woods, L., Wuyts, S., Xiao, C., Xue, L. C., IMMREP25 Participant Consortium,, Barton, J., Noakes, M., May, D. H., Peters, B."
date: 2026-04-01
pdf: "https://www.biorxiv.org/content/10.64898/2026.03.30.715276v1.full.pdf"
tags: ["query:gentcr"]
score: 9.0
evidence: "预测TCR:pMHC结合并评估模型在未见肽段上的表现"
tldr: "本研究通过IMMREP25竞赛系统评估了预测TCR与未见肽MHC结合的最新算法表现。研究聚焦于没有实验数据支持的未知肽，汇集126个不同模型，测试1,000个TCR与20个未见肽的结合预测。结果显示部分方法显著优于随机，尤其是结合结构建模的模型，标志着该领域取得实质性进展。"
source: biorxiv
selection_source: fresh_fetch
figures_json: "[{\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-03-30-715276-v1/fig-001.webp\", \"caption\": \"Table 1: The 20 peptides represented in this dataset, described by their HLA context, source organism, minimum Levenshtein distance to any published epitope, and maximum shared substring with any published epitope.\", \"page\": 5, \"index\": 1, \"width\": 981, \"height\": 741}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-03-30-715276-v1/fig-002.webp\", \"caption\": \"Table 2: structural methods were well-represented among the methods with macro-AUC_0.1 ≥ 0.52 (only the top method per team is described). There was a further distinction between methods that used AF3 for TCR-pMHC modelling and alternatives such as Chai-1 and Boltz-1. *Methods details and scores are shown for the top submission for the team in question, as multiple teams submitted closely-related methods. Supplementary Figure 3 and 4 show performance across all models submitted, and perpeptide and macro scores are found in Supplementary File 1.\", \"page\": 12, \"index\": 2, \"width\": 981, \"height\": 562}]"
motivation: pMHC结合预测方法在未见肽场景下的能力。
method: "研究通过IMMREP25竞赛测试了126个方法在1,000个TCR和20个未见肽上的预测表现。"
result: 最佳方法宏观AUC_0.1为0.60，显著优于随机预测。
conclusion: 结果显示结构建模对于提高未见肽预测准确度至关重要，但预测任务仍充满挑战。
---

## 摘要
T细胞受体（TCR）能够与由MHC分子呈递的肽（pMHC）结合，这是触发T细胞反应的第一步。可靠的TCR:pMHC结合预测方法在临床诊断、治疗以及分子相互作用的基础研究中都有广泛应用。IMMREP是一项由社区组织的预测竞赛系列，要求参与者在未公开的数据集上预测TCR:pMHC结合。先前在2022年和2023年的竞赛结果显示，对于已有实验数据的肽（“已知”肽），多种方法能够以显著的准确度预测TCR-pMHC结合（中位数AUC_0.1[≥]0.7）。相比之下，对于没有相关数据的肽（“未知”肽），模型的表现并未优于随机猜测。本文报告了IMMREP25的结果，该轮竞赛专注于未知肽，以评估该领域的最新进展。我们共收到了126个命名提交，用于预测1000个TCR与20个未知肽的特异性，这些肽由两种MHC分子（HLA-A*02:01和HLA-B*40:01）限制。表现最佳的方法实现了macro-AUC_0.1为0.60的成绩，显著优于随机预测，表明该领域取得了重要进步。顶尖方法将结构建模融入预测过程中，显示出对于未知肽而言，结构理解能促进TCR:pMHC相互作用的预测。本次基准测试结果突显了TCR:pMHC预测仍面临的重要挑战，并将为未来方法的发展提供参考。

## Abstract
T cell receptors (TCRs) can bind to peptides presented by MHC molecules (pMHC) as a first step to trigger a T cell response. Reliable approaches to predict TCR:pMHC binding would have broad applications in clinical diagnostics, therapeutics, and the fundamental understanding of molecular interactions. IMMREP is a community organized series of prediction contests that asks participants to predict TCR:pMHC binding on unpublished datasets. Previous iterations in 2022 and 2023 showed multiple approaches can predict TCR-pMHC binding with significant accuracy (median AUC_0.1[&ge;]0.7) for peptides where experimental data is available ("seen" peptides). In contrast, models did not outperform random guessing for peptides that have no such data available ("unseen" peptides). Here we report on the results of IMMREP25, which focused solely on unseen peptides in order to evaluate the cutting edge of the field. We received 126 named submissions predicting the specificity of 1,000 TCRs against twenty unseen peptides restricted by one of two MHC molecules (HLA-A*02:01 and HLA-B*40:01). The best performing methods showed a macro-AUC_0.1 of 0.60, significantly better than random, demonstrating significant advances in the field. The top performing methods incorporated structural modeling into their approach, indicating that especially for  unseen peptides, a structural understanding aids in the prediction of TCR:pMHC interactions. The results from this benchmark highlight the significant challenges remaining for TCR:pMHC predictions and will inform future method development.

---

## 论文详细总结（自动生成）

# IMMREP25：未知肽 — 深度结构预测在TCR:pMHC结合中的基准评估

---

## 一、研究核心问题与背景

* **问题背景**：T细胞受体（TCR）通过识别由主要组织相容性复合物（MHC）呈递的肽（形成pMHC复合体）来触发免疫反应。了解哪些TCR能与哪些pMHC结合，对疫苗设计、癌症免疫治疗和自身免疫疾病诊断具有核心意义。
* **研究动机**：当前机器学习和序列匹配方法在预测“已知肽”上的表现较好，但当肽序列未出现在任何训练集（“未知肽”）中时，预测效果几乎退化为随机猜测。
* **整体目标**：本研究通过社区竞赛 **IMMREP25**，全面评估不同方法在预测 **未知肽** 场景下的TCR:pMHC结合能力，推动真实跨肽泛化能力的提升。

---

## 二、方法论与技术框架

### 1. 核心思想
* 采用开放竞赛形式（Kaggle平台），汇集全球研究团队提交的模型预测结果，形成学术领域的客观 benchmark。
* 将评估重点从“已见肽”转向 **完全未见的肽序列**，测试模型的真正泛化能力。
* 通过统一指标（macro-AUC₀.₁），量化模型在低假阳率区间的预测效果。

### 2. 关键技术路线
不同团队提交的算法方法大致分为以下几类：

#### （1）结构建模类方法
* 主流代表：**AlphaFold3（AF3）、Chai-1、Boltz-1、TCRmodel2、SwiftTCR**。
* 流程：  
  - 利用结构预测模型生成TCR-pMHC复合物的三维结构；  
  - 计算模型内部信心指标（如ipTM、pLDDT、PAE）作为结合评分；  
  - 对多个模型输出进行聚类或评分归一化，生成最终预测值。  
* 示例：  
  - **Bradley方法（AF3-TCRDock）**：利用AF3三维结构预测，提取pLDDT平均值并去均值归一化。  
  - **Pierce方法**：基于预测对齐误差（PAE），并添加TCR聚类机制。  
  - **Altin方法**：以AF3预测的TCR-肽界面平均PAE作为打分。  
  - **Wang方法**：直接使用AF3生成的iPTM值作为绑定预测分数。

#### （2）序列与语言模型类方法
* 代表：**TAPIR3（ESM微调）、STAPLER（K-means+KNN）**。
* 流程：利用蛋白语言模型（ESM）或变换器模型提取序列特征，再通过神经网络或聚类方法输出结合概率。
* TAPIR3为混合方式，属于结构指标知识蒸馏（将AF3/Chai-1结构信息压缩进ESM编码）。

#### （3）统计势能与物理模型类
* 如 **TCRen**（基于氨基酸接触势能）、**HERMES**（基于原子环境与ΔΔG势能调整）。
* 从预测结构中计算能量分布与结合稳定性估计。

### 3. 评估指标与计算公式
* **主要指标**：Macro-AUC₀.₁（限制假阳率≤10%区域的ROC曲线下面积）。
* **计算方式**：  
  - 每个pMHC单独计算AUC₀.₁；  
  - 对所有私有测试肽（n=18）取宏平均；
  - 采用 `scikit-learn` 的 `roc_auc_score` 和 `average_precision_score` 作为实现。

---

## 三、实验设计与Benchmark设置

### 1. 数据集构建
* **数据来源**：由 Adaptive Biotechnologies 专门生成的新型实验数据。
* **规模与内容**：
  - 1,000个独立TCR序列；
  - 20个未公开肽（9-mer肽），来源于病毒蛋白；
  - 2种MHC限制：HLA-A*02:01 与 HLA-B*40:01；
  - 共 8,938 条记录（阳性 1,000 条，阴性 7,938 条）。
* **验证策略**：
  - 公共排行榜使用2个已公开的肽；
  - 私有排行榜使用剩余18个肽，以防模型“验证泄漏”。

### 2. Benchmark内容
* 共收到 **126个命名提交**，来自多个国际研究机构。
* 对比方法包含结构模型（AF3 / Chai-1 / TCRdock 等）、语言模型（ESM / TAPIR系列）以及统计势能法（TCRen / HERMES）。
* 最终筛选出成绩宏观AUC₀.₁ ≥ 0.52 的前15种方法列入分析。

---

## 四、资源与算力

* 文中无统一的算力报告，但部分方法（例如AF3、Chai-1、Boltz-1）在描述中提到使用 **MSA多序列比对、五种seed并行建模**，暗示高并行GPU计算需求。
* 另有方法使用 **VSC超级计算中心（Boltz-1运行）** 或分布式集群（Chai-1结构预测），但未列出具体GPU型号、数量或运行时长。
* 结论：**算力信息未统一公开**，仅能确认结构类模型对计算资源需求极高。

---

## 五、实验数量与充分性

* 单轮竞赛持续21天（每队每日可提交一次），共评测 126 个不同模型。
* 每个模型在同一数据集上测评，保证公平。
* 还额外分析 **聚类版与原始版模型** 的性能差异，以检验数据结构利用的影响。
* 整体来看：
  - 覆盖所有主流建模范式（结构、语言模型、势能）；  
  - 指标统一，评估客观且可重复；
  - 由于为竞赛型实验，未含传统消融设计，但方法覆盖度充分。

---

## 六、主要结论与发现

* **总体表现**：绝大多数方法仍接近随机水平（AUC₀.₁≈0.50），但有少数方法显著突破。
* **最佳成绩**：Bradley（AF3-TCRDock）方法宏观AUC₀.₁ = **0.601**，显著优于随机（p<0.05）。
* **关键发现**：
  - 结构建模显著优于纯序列模型；
  - 对“未见肽”场景，结构信心指标（如pLDDT、PAE、iPTM）能提供有效区分；
  - HLA-A*02:01 上预测优于 HLA-B*40:01（可能因公众数据分布差异造成训练不均衡）。
* **趋势**：TCR:pMHC预测领域正从序列学习向 **高分辨率结构建模与知识蒸馏** 转型。

---

## 七、优点与亮点

* **全面性**：数据完全由实验获得，肽与已知数据库保持≥4位Levenshtein距离，避免数据泄露。
* **公平评测机制**：公私排行榜设计防止测试集偏倚。
* **结构创新**：首次将AlphaFold3应用于TCR:pMHC预测，并验证AF3信心指标的效力。
* **跨团队协作**：包括机器学习、结构生物学与免疫学多领域研究者共同参与。
* **前瞻性**：提出了未来潜在方向——结构信息的轻量级蒸馏模型（如TAPIR3），解决高算力问题。

---

## 八、不足与局限

* **算力瓶颈**：AF3等结构方法计算代价极高，难以在大规模TCR库中应用。
* **泛化限制**：虽然有改进，但宏观AUC仍仅为0.6，离实际应用仍远。
* **数据偏差**：HLA-B*40:01样本量极少（训练集中仅几十个），导致模型在该类MHC上表现不稳定。
* **缺乏消融分析**：作为竞赛报告，重点在方法比较，未系统探究特征贡献或参数敏感性。
* **聚类利用风险**：部分团队利用数据结构信息提高分数，可能削弱模型泛化真实性。

---

**结论总述**：  
IMMREP25首次系统性展示了未知肽场景下TCR:pMHC结合预测的全球现状。结构建模方法，特别是AlphaFold3衍生算法，在此任务上证明了显著优势，但计算成本高及泛化能力有限仍为普遍挑战。该基准数据和结果为后续研究提供了标准参照和发展方向。

---

（完）
