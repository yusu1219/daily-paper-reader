---
title: "FairTCR: Equity-Aware TCR--pMHC Binding Prediction\\\\Across HLA Alleles and Cohort Strata"
title_zh: FairTCR：关注公平性的跨 HLA 等位基因与队列分层的 TCR–pMHC 结合预测
authors: "Nowak, P., Kowalski, J., Lewandowski, T."
date: 2026-04-17
pdf: "https://www.biorxiv.org/content/10.64898/2026.04.14.718511v1.full.pdf"
tags: ["query:gentcr"]
score: 8.0
evidence: 跨等位基因的TCR-pMHC结合预测与优化
tldr: 本研究针对TCR–pMHC结合预测中由于数据偏倚造成的公平性问题，提出FairTCR方法，基于群体分布鲁棒优化减少不同HLA等位基因和队列间的性能差距。在VDJdb–IEDB基准上，FairTCR在不损失整体准确性的情况下，显著提升了稀有等位基因和少数群体的预测公平性。
source: biorxiv
selection_source: fresh_fetch
figures_json: "[{\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-04-14-718511-v1/fig-001.webp\", \"caption\": \"TABLE II DATASET AND SPLIT SUMMARY (ALL HLA SUPERTYPES COMBINED).\", \"page\": 3, \"index\": 1, \"width\": 529, \"height\": 352}]"
motivation: 现有TCR–pMHC结合预测数据偏向少数常见HLA等位基因和欧洲血统群体，导致模型在稀有群体上的性能不公。
method: 采用基于群体分布鲁棒优化（GDRO）的框架，通过在线指数梯度更新最小化HLA超型和队列层次的最坏组损失。
result: "FairTCR将平均与最差群体AUPRC差距从0.190降至0.098，实现48.4%的差距减少，并保持整体性能。"
conclusion: FairTCR显著提升稀有等位基因组和代表性不足人群的预测公平性。
---

## 摘要
公共 TCR–pMHC 结合数据库严重偏向于少数几个研究较充分的 HLA 等位基因——尤以 HLA-A*02:01 为代表，其约占经整理记录的 45%——并且样本主要来自欧洲血统队列。基于此类数据训练的标准经验风险最小化（ERM）模型在总体精度上表现良好，但在稀有等位基因和代表性不足的队列上性能显著下降，从而造成单一指标基准测试中难以察觉的系统性差异。我们提出了 FairTCR，一种群体分布鲁棒优化（GDRO）框架，通过在线指数梯度更新，在 HLA 超型及队列分层间最小化最差组损失。FairTCR 将在经整理的 VDJdb–IEDB 基准上的平均–最差组 AUPRC 差距从 ERM 的 0.190 降至 0.098，减少差距幅度达 48.4%，同时保持具有竞争力的平均 AUPRC（0.432 对比 ERM 的 0.431）。针对各 HLA 的分析显示，稀有等位基因组（如 B*08:01、B*44:02）AUPRC 提升最高可达 0.062，有效改善了对代表性不足患者群体的计算预筛查公平性。

## Abstract
Public TCR--pMHC binding databases are heavily skewed toward a handful of well-studied HLA alleles---most prominently HLA-A*02:01, which covers $\sim$45\% of curated records---and toward patients from European-ancestry cohorts. Standard empirical risk minimization (ERM) trained on such data achieves strong pooled accuracy but routinely underperforms on rare alleles and underrepresented cohorts, creating systematic disparities that are invisible in single-metric benchmarks. We introduce \emph{FairTCR}, a group distributionally robust optimization (GDRO) framework that minimizes worst-group loss across HLA supertypes and cohort strata via online exponentiated gradient updates. FairTCR reduces the average--worst-group AUPRC disparity from 0.190 (ERM) to 0.098 on a curated VDJdb--IEDB benchmark, achieving a 48.4\% disparity reduction while maintaining competitive average AUPRC (0.432 vs.\ 0.431 for ERM). Per-HLA analysis shows that rare allele groups (B*08:01, B*44:02) gain up to 0.062 AUPRC points, directly improving the equity of computational pre-screening for underrepresented patient populations.

---

## 论文详细总结（自动生成）

# FairTCR：关注公平性的跨 HLA 等位基因与队列分层的 TCR–pMHC 结合预测

---

## 一、核心问题与研究背景

- **研究动机**：当前 TCR–pMHC 结合预测模型在公共数据库（如 VDJdb、IEDB）上表现优异，但这些数据库样本严重偏向少数高频的 HLA 等位基因（尤以 *HLA-A*02:01* 为主，占约 45%），且样本主体来自欧洲血统群体。
- **问题本质**：这种数据偏倚导致标准经验风险最小化（ERM）模型虽在总体精度上表现良好，却在稀有等位基因与少数群体上显著失效，形成 **系统性预测不公平**。
- **研究目标**：提升模型在多 HLA 等位基因和群体分层（cohort strata）上的性能公平性，使预测结果更加均衡可靠。

---

## 二、方法论：FairTCR 框架

- **核心思想**  
  将“群体公平性”作为学习目标，通过 **群体分布鲁棒优化（Group Distributionally Robust Optimization, GDRO）** 最小化最差组（worst-group）的预测损失，减少不同群体间性能差距。

- **技术要点**  
  1. **分组定义**：以 HLA 超型（supertypes）和队列（cohort）为分组粒度。  
  2. **目标函数**：优化最坏群体的加权损失，而非总体平均损失。  
  3. **优化策略**：采用 **在线指数梯度更新（online exponentiated gradient updates）**，动态调整每个群体的损失权重，使优化方向倾向于表现最差的群体。  
  4. **训练框架**：总体保持与 ERM 模型相同的神经网络结构，仅修改训练目标与梯度更新过程。

- **算法流程（文字描述）**  
  1. 初始化各群体权重（均匀分布）。  
  2. 在每轮训练中计算各群体的损失。  
  3. 对群体权重进行指数更新，使高损失群体获得更高梯度影响。  
  4. 持续最小化加权后的最坏组损失，直到收敛。  
  5. 输出在群体层面鲁棒的最终模型。

---

## 三、实验设计

- **数据来源与场景**  
  - 使用整理后的 **VDJdb–IEDB 基准数据集**，包含多种 HLA 等位基因样本。  
  - 结合 HLA 超型和队列分层进行公平性分析。

- **基准与对比方法**  
  - **基准方法**：标准 ERM 模型。  
  - **对比维度**：平均 AUPRC、最差群体 AUPRC、平均–最差群体性能差距。

- **评估指标**  
  - 主要指标：AUPRC（Area Under Precision–Recall Curve）。  
  - 特别关注指标：平均–最差群体 AUPRC 差距，衡量公平性提升。

---

## 四、资源与算力

- **文中未明确说明算力细节**（如 GPU 型号、数量、训练时长等）。
- 可能基于常规深度学习环境（推测为单卡或多卡 GPU）实现 GDRO 优化。
- 建议未来工作明确实验硬件与资源消耗以增强复现性。

---

## 五、实验数量与充分性

- **实验内容**  
  - 在 VDJdb–IEDB 基准上进行系统对比。  
  - 分别评估平均性能与最差群体性能变化。  
  - 对稀有等位基因（如 *B*08:01*, *B*44:02*）进行单独分析。

- **实验结果充分性**  
  - 涵盖多群体与多等位基因分层，验证模型公平性提升。  
  - 未明确提及其他独立数据集或消融实验，因此可能缺乏对泛化性和算法成分的深入拆解。  
  - 整体实验公平性较高，对比指标客观、结果显著。

---

## 六、主要结论与发现

- FairTCR 成功降低群体间性能不均：
  - 平均–最差群体 AUPRC 差距从 **0.190（ERM）降至 0.098（FairTCR）**，减少 **48.4% 差距**。
  - 平均 AUPRC 几乎保持不变（0.432 vs 0.431）。
- 稀有等位基因的预测性能明显改善：
  - *B*08:01*、*B*44:02* 等群体的 AUPRC 提升最高达 **0.062**。
- 模型在保持整体精度的同时显著提升了预测公平性，对代表性不足群体具有实际应用价值。

---

## 七、优点

- **公平性导向学习目标**：从平均性能转向最坏群体性能，体现 AI 公平性的算法化实现。
- **数学框架稳健**：基于 GDRO 的优化方法具有理论可解释性。
- **性能与公平性兼顾**：在不牺牲整体准确性的前提下，显著减少性能差距。
- **应用价值高**：对免疫组学与精准医疗中群体偏差问题提供了可行解决方案。

---

## 八、不足与局限

- **算力与复现性未知**：未提供硬件与训练细节。
- **实验覆盖有限**：仅在单一基准上评估，尚未测试跨数据库或独立临床数据。
- **可拓展性**：GDRO 方法依赖群体标签定义，若群体分类不准确，可能影响优化有效性。
- **公平性评价维度单一**：以性能差距为主，未涉及潜在群体误差分布或社会性公平指标。

---

（完）
