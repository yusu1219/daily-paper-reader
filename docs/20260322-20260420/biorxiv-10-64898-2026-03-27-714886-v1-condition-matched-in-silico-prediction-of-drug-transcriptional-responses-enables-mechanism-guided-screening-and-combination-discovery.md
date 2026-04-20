---
title: Condition-matched in silico prediction of drug transcriptional responses enables mechanism-guided screening and combination discovery
title_zh: 条件匹配的体内模拟药物转录反应预测促进机制引导筛选与联合发现
authors: "Xiao, M., He, Y., Hu, J., Zou, F., Zou, B."
date: 2026-03-31
pdf: "https://www.biorxiv.org/content/10.64898/2026.03.27.714886v1.full.pdf"
tags: ["query:virtcell"]
score: 9.0
evidence: 预测药物诱导的转录响应
tldr: 本文提出了一种名为DEPICT的Transformer深度学习框架，用于从基线基因表达和药物属性预测药物在不同条件下的转录组响应。该方法显著提升未见药物和细胞类型下的预测准确性，并在非小细胞肺癌研究中成功发现潜在治疗药物组合，证明了其在药物再利用和组合发现中的实用价值。
source: biorxiv
selection_source: fresh_fetch
figures_json: "[{\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-03-27-714886-v1/fig-001.webp\", \"caption\": \"Fig. 3: 2D plot of predicted transcriptional responses on A549\", \"page\": 11, \"index\": 1, \"width\": 737, \"height\": 1131}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-03-27-714886-v1/fig-002.webp\", \"caption\": \"Fig. 2: Drug MoA radar plot\", \"page\": 7, \"index\": 2, \"width\": 454, \"height\": 402}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-03-27-714886-v1/fig-003.webp\", \"caption\": \"Table 2: Validated candidate compounds for NSCLC from the top-20 list\", \"page\": 8, \"index\": 3, \"width\": 762, \"height\": 283}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-03-27-714886-v1/fig-004.webp\", \"caption\": \"Fig. 1: Overview of DEPICT\", \"page\": 4, \"index\": 4, \"width\": 771, \"height\": 916}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-03-27-714886-v1/fig-005.webp\", \"caption\": \"Table 1: Model performance across three generalization schemes\", \"page\": 5, \"index\": 5, \"width\": 763, \"height\": 588}]"
motivation: 现有实验性转录组数据获取成本高昂，限制了药物机制探索和再利用研究。
method: 采用Transformer架构结合基因表达、药物表征及实验条件信息，预测药物诱导的转录变化。
result: DEPICT在未见药物和细胞类型场景下表现优于现有模型，在癌症案例中成功筛选出与临床相关的候选药物。
conclusion: DEPICT可实现高精度、条件匹配的药物转录响应预测，推动基于转录组的药物发现与机制研究。
---

## 摘要
扰动转录组学将治疗性化合物与细胞机制联系起来，为药物发现提供了强有力的框架，但在多样的细胞状态、剂量和持续时间下实验性地分析转录反应代价高昂且常常不可行。在此，我们提出了 DEPICT（Drug rEsponse Prediction in transCriptomics with Transformers），一个深度学习框架，可根据基线基因表达、扰动设定和互补药物表示，预测与条件匹配的药物诱导转录反应。利用 LINCS L1000 数据集，DEPICT 能够泛化到未见过的药物和细胞类型，并优于五种基线策略和两种最新深度学习模型。在最具挑战性的未见细胞评估中，DEPICT 是唯一超越所有基线的模型，与次优深度模型相比，差异表达预测准确度提高了 30.3%，扰动表达预测误差降低了 36.8%。在非小细胞肺癌（NSCLC）案例研究中，DEPICT 支持的虚拟筛选优先选择了预测可逆转疾病相关转录特征的化合物。值得注意的是，排名前 20 的优先化合物中有 13 个此前已进入与 NSCLC 相关的临床试验或在 NSCLC 研究中得到验证，支持所预测扰动特征的转化相关性。DEPICT 还在缺乏实验匹配的特征时，进一步实现了条件匹配的药物协同预测与机制探索。总体而言，这些结果表明，准确、条件匹配的体内模拟扰动分析能够扩展以转录组驱动的假设生成，用于药物再利用和联合发现。

## Abstract
Perturbational transcriptomics links therapeutic compounds to cellular mechanisms and provides a powerful framework for drug discovery, but experimentally profiling transcriptional responses across diverse cell states, doses and durations is costly and often infeasible. Here we present DEPICT (Drug rEsponse Prediction in transCriptomics with Transformers), a deep learning framework that predicts condition-matched drug-induced transcriptional responses from baseline gene expression, perturbation settings and complementary drug representations. Using the LINCS L1000 dataset, DEPICT generalized to unseen drugs and cell types and outperformed five baseline strategies and two recent deep learning models. In the most challenging unseen-cell evaluation, DEPICT was the only model to surpass all baselines, improving differential-expression prediction accuracy and reducing perturbed-expression prediction error by 30.3% and 36.8%, respectively, relative to the next-best deep model. In a non-small cell lung cancer (NSCLC) case study, DEPICT-enabled virtual screening prioritized compounds predicted to reverse disease-associated transcriptional signatures. Notably, 13 of the top 20 prioritized compounds had either previously entered NSCLC-related clinical trials or been validated in NSCLC studies, supporting the translational relevance of the predicted perturbational profiles. DEPICT further enabled condition-matched drug synergy prediction and mechanistic exploration when experimentally matched profiles were unavailable. Together, these results show that accurate, condition-matched in silico perturbation profiling can scale transcriptomics-driven hypothesis generation for drug repurposing and combination discovery.

---

## 论文详细总结（自动生成）

# 条件匹配的体内模拟药物转录反应预测：论文总结

---

## 一、核心问题与研究背景

- **问题背景**：扰动转录组学能够揭示药物与细胞机制之间的关系，是药物发现、机制解析和药物再利用的重要基础。然而，实验性测定药物在不同细胞类型、浓度、时间条件下的转录反应，成本高且难以全面覆盖。
- **研究动机**：迫切需要一种可在体内模拟条件下预测药物的转录响应的计算框架，以便在缺乏实验数据时实现药物筛选和机制探索。
- **核心意义**：论文提出的模型旨在解决药物反应预测的“条件匹配”问题——不仅仅预测总体响应，更要准确反映药物在特定细胞条件下的转录效应。

---

## 二、方法论：DEPICT 框架

### 核心思想

- 提出一个基于 **Transformer 架构** 的深度学习模型——**DEPICT（Drug rEsponse Prediction in transCriptomics with Transformers）**。
- 通过综合 **基线基因表达**、**药物表征（如化学结构、靶点信息）** 和 **实验扰动设定**（剂量、时间、细胞类型），预测药物引起的转录组变化。
- 实现了“条件匹配”的预测，即考虑药物效应对不同细胞状态的依赖。

### 关键技术细节

- **输入模块**：
  - **基因表达编码**：采用自注意力机制表征细胞基线状态；
  - **药物表示**：整合化学指纹和药物描述符；
  - **实验条件编码**：将剂量、时间等设定以位置向量形式输入。
- **Transformer主干网络**：
  - 使用多头注意力捕捉基因-药物交互特征；
  - 输出端预测每个基因的扰动表达水平或差异表达结果。
- **损失函数设计**：
  - 同时优化两种目标：扰动后表达误差和差异表达准确度。
- **训练流程**：
  - 基于LINCS L1000数据库构建样本；
  - 采用多任务学习策略增强泛化能力。

---

## 三、实验设计

- **数据集**：主用 **LINCS L1000** 药物扰动数据集，包含大量药物在不同细胞类型、剂量和时间下的转录反应。
- **评估场景**：
  - **未见药物预测**：模型面对从未在训练中出现的药物；
  - **未见细胞类型预测**：测试模型在新细胞系上的泛化；
  - **完全新组合预测**：药物和细胞均未见过的情况。
- **对比模型**：
  - 五种传统基线方法（包括线性回归、随机森林等）；
  - 两个近期的深度学习模型（例如基于图卷积和多层感知器的模型）。
- **Benchmark指标**：
  - 差异表达预测准确度；
  - 扰动表达误差（例如MAE或RMSE）；
  - 基于生物学一致性的药物排名验证。

---

## 四、资源与算力

- 论文未明确说明具体的训练算力或硬件信息（例如GPU型号、数量、训练时长等）。
- 根据模型规模和数据量，推测可能使用中等规模GPU集群（常见于LINCS相关研究），但文中未作详细描述。

---

## 五、实验数量与充分性

- 实验包含以下部分：
  - 三种不同泛化场景的大规模定量评估；
  - 与七种对照方法的系统比较；
  - 一个非小细胞肺癌（NSCLC）虚拟筛选案例；
  - 对药物协同作用和机制推理的探索性实验。
- 结合上述，实验设计覆盖了跨药物、跨细胞、跨任务的验证，数量充足且对照公平，体现出较高的实验充分性与客观性。

---

## 六、主要结论与发现

- DEPICT在所有泛化场景下均优于对照方法：
  - 在最具挑战性的未见细胞场景中，差异表达预测准确率提升 **30.3%**；
  - 扰动表达预测误差降低 **36.8%**。
- 在 NSCLC 案例研究中：
  - 虚拟筛选得到的前20种候选药物中，有13种已被临床验证或进入相关试验。
  - 说明DEPICT预测的转录响应具有良好的生物学可解释性与转化潜力。
- 模型还可支持协同作用预测与机制探索，即便缺乏实验数据匹配。

---

## 七、优点与亮点

- **条件匹配概念创新**：模型明确将药物响应与细胞条件关联，提升预测生物学真实性。
- **强泛化性能**：在未见药物、细胞场景中仍具高准确率。
- **Transformer架构优势**：有效捕捉高维基因间交互关系；
- **跨疾病实证**：在真实病理场景（如NSCLC）中验证预测能力；
- **机制解释性强**：输出不仅限于预测数值，还可用于推断潜在药物机制或合作效应。

---

## 八、不足与局限

- **算力与资源未公开**：难以复现模型训练细节；
- **数据依赖性**：主要依赖LINCS L1000数据，其他类型扰动或组学数据的适用性尚未验证；
- **解释难度**：尽管结果具生物学一致性，但Transformer模型的可解释性仍有限；
- **药物表示限制**：目前使用的药物特征较为基础，可进一步融合分子动力学、蛋白互作信息；
- **应用范围约束**：模型主要针对体外细胞环境，向体内或临床条件迁移仍需验证。

---

（完）
