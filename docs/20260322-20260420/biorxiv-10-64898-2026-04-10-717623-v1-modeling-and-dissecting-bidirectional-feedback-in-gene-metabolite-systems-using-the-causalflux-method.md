---
title: Modeling and dissecting bidirectional feedback in gene-metabolite systems using the CausalFlux method
title_zh: 利用 CausalFlux 方法对基因–代谢物系统中的双向反馈进行建模与解析
authors: "Subramanian, N., Kumar, S. P., Rengaswamy, R., Bhatt, N. P., Narayanan, M."
date: 2026-04-13
pdf: "https://www.biorxiv.org/content/10.64898/2026.04.10.717623v1.full.pdf"
tags: ["query:virtcell"]
score: 9.0
evidence: 预测基因敲除条件下的稳态反应通量
tldr: 本文提出CausalFlux方法，以整合基因调控与代谢网络，首次系统建模基因与代谢物间的双向反馈。通过因果手术与约束分析迭代预测细胞稳态通量，结果显示双向反馈能显著提升通量和基因本质性预测的准确性，推动系统生物学模型的发展。
source: biorxiv
selection_source: fresh_fetch
figures_json: "[{\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-04-10-717623-v1/fig-001.webp\", \"caption\": \"Fig 2. FVA max as best CausalFlux variant on TMs: (A) Topology of TM1 (integrated GRN-GSMM system; see S1 Fig. for the topology of TM2 and TM3). (B-C) Scatter plots between the normalized predicted and actual fluxes for TM1 under the 320 exchange rate for “X” and “A” gene KOs, where predictions are by CausalFlux’s FBA and FVA (min and max) variants. Spearman’s ρ and associated p-value are also shown atop each plot. (D) Scatter plots (with jitter of 0.05 units) of the ρ computed between different CausalFlux variants’ predicted and actual fluxes for each of the 39 TM cases. (E) Different simulation scenarios/cases for each TM and associated correlation tests performed (points in plot D) are listed.\", \"page\": 6, \"index\": 1, \"width\": 773, \"height\": 813}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-04-10-717623-v1/fig-002.webp\", \"caption\": \"Fig 3. Comparing CausalFlux, TRIMER and GIMME on TMs: (A) Scatter plot (with jitter of 0.05 units) of ρ computed between CausalFlux (FVA max) and actual (vs.) TRIMER and actual for all the WT/KO cases across all TMs under different exchange rates. (B) Similar plot as (A) but with TRIMER replaced by GIMME (FVA max). (C) and (D) are the same as (A) and (B), respectively, but the points are colored based on the exchange rates. (E), (F), and (G) Actual vs predicted (CausalFlux (FVA max), TRIMER, and GIMME (FVA max) respectively) fluxes of the biomass reaction across the WT/KO cases in all TMs under different exchange rates.\", \"page\": 7, \"index\": 2, \"width\": 524, \"height\": 996}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-04-10-717623-v1/fig-003.webp\", \"caption\": \"Fig 5. Exploring the role of metabolic feedback through ablation studies: (A) Five different ablation studies were performed by removing the metabolite feedback edges to gene(s) that have high influence on single-gene KOs. Information on genes misclassified as essential after ablation are also shown. (B) Illustration of the fourth ablation study (fourth row) shown in panel A. (C and D) Scatter plot (with default jitter) showing the biomass of the 798 single-gene KOs before vs. after removal of feedback edges to: the gene crp (panel C); and the 10 metabolic feedback genes with the most influence on single-gene KOs (panel D).\", \"page\": 10, \"index\": 3, \"width\": 785, \"height\": 754}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-04-10-717623-v1/fig-004.webp\", \"caption\": \"Fig 7. CausalFlux predictions under different media conditions: (A, B) Each is a scatter plot (with jitter 0.1 units) of predicted growth rate (biomass) under the two indicated media conditions. (C) Bar plot showing the number of predicted essential genes (predicted growth rate of zero) under the indicated media conditions. Common genes (orange) represent the number of predicted essential genes shared across all media conditions.\", \"page\": 14, \"index\": 4, \"width\": 771, \"height\": 249}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-04-10-717623-v1/fig-005.webp\", \"caption\": \"Fig 1. Overview of our CausalFlux method: (A) CausalFlux integrates GRN model and GSMM using prior knowledge on two-way feedback interactions between them, in an iterative fashion. (B) A key step in CausalFlux is performing causal surgery on a conditioning variable like gene “C” (which may be a transcription factor in the GRN) – incoming edges from the parents of “C” (“A” and “B”) are severed to obtain a mutilated GRN, and “C”’s value forced to 1 to reflect activation feedback from M2 metabolite. Conditional probability of “D” before and after causal surgery is shown. (C) CausalFlux flowchart (see Algorithm 1 and Methods for details; FVA is flux variability analysis). (D & E) Comparison of predictive performance of CausalFlux vs. one-way feedback method TRIMER (or GIMME) on: (D) three testbed GRN+GSMM integrated models, with fluxes simulated using ODEs under various exchange rates and gene KOs (ODE is Ordinary Differential Equation); and (E) real-world E. coli model, with growth/no-growth outcomes measured under 798 single-gene KOs.\", \"page\": 4, \"index\": 5, \"width\": 654, \"height\": 855}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-04-10-717623-v1/fig-006.webp\", \"caption\": \"Fig 6. Benchmarking CausalFlux on PROM and rFBA datasets: (A) Scatter plot (with jitter 1.75 units) between the accuracy computed between CausalFlux predictions and Actual vs. the accuracy between rFBA predictions and Actual for the 100 media conditions. (B) Scatter plot (with jitter 1.75 units) between the accuracy computed between CausalFlux predictions and Actual vs. the accuracy between PROM predictions and Actual for the 100 media conditions. (C) Performance comparisons of CausalFlux and rFBA for the various Carbon sources, Nitrogen sources and Double-Nitrogen sources and overall 100 media conditions. (D) Performance comparisons of CausalFlux and PROM for the various Carbon sources, Nitrogen sources and Double-Nitrogen sources and overall 100 media conditions. (E) Comparison of classification metrics (TP: true positives [essential], FN: false negatives, FP: false positives, TN: true negatives [non-essential]) for CausalFlux applied to the rFBA and PROM datasets (usual definition of essential/non-essential), along with Random Classifier, rFBA, and PROM predictions across 1500 data points (100 media conditions × 15 gene KOs).\", \"page\": 12, \"index\": 6, \"width\": 766, \"height\": 862}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-04-10-717623-v1/fig-007.webp\", \"caption\": \"Fig 4. Comparing CausalFlux and TRIMER on E. coli datasets: (A) Comparing the performances of CausalFlux, TRIMER, and a random classifier for predicting growth/no growth in 798 single-gene KO cases in E. coli. (B) Comparing the predictions and (C) metrics for CausalFlux across 0th, 1st iterations and after the algorithm had converged to show the effect of metabolic feedback. Note: True positives: essential genes predicted as essential; True negatives: non-essential genes predicted as non-essential; False positives: non-essential genes predicted as essential; and False negatives: essential genes predicted as non-essential.\", \"page\": 9, \"index\": 7, \"width\": 609, \"height\": 633}]"
motivation: 现有模型主要描述从基因到代谢单向调控，但忽视了代谢物对基因的反向调控。
method: 提出CausalFlux方法，结合贝叶斯基因调控网络与约束代谢模型，通过迭代因果干预模拟双向反馈。
result: CausalFlux在预测反应通量和E.coli基因敲除生长表型方面优于TRIMER，相关性与准确性均显著提升。
conclusion: 研究证明在建模基因与代谢的相互反馈时，考虑双向反馈能显著提高预测精度和生物意义。
---

## 摘要
预测细胞行为是系统生物学和代谢工程中的核心任务，可以通过整合基因调控和代谢等过程的建模得到改进。尽管从基因调控（通过基因调控网络建模）到代谢（通过全基因组尺度代谢模型建模）的信息流研究已有较深探索，但代谢物对基因的反向调控仍较少研究。我们提出 CausalFlux 方法来模拟基因与代谢物之间的双向反馈，以便在野生型（WT）或扰动条件（例如基因敲除/KO）下预测稳态反应通量。CausalFlux 通过对贝叶斯基因调控网络的因果手术与耦合代谢模型的基于约束分析迭代实现这一过程。通过与当前最先进的基因到代谢物单向反馈模型 TRIMER 进行比较，CausalFlux 使我们能够评估双向反馈在多个测试模型和实际生物系统中的影响。相较于 TRIMER，引入双向反馈的 CausalFlux 在 39 种不同仿真条件中，有 92% 的情况下提高了实际与预测通量之间的 Spearman 相关系数。在预测大肠杆菌单基因 KO 后的生长/不生长表型时，CausalFlux 在鉴定必需基因方面达到了平衡准确率 0.79，而 TRIMER 为 0.71，再次凸显了双向反馈建模的重要性。在进一步解析大肠杆菌中特定代谢物→基因反馈边作用的消融研究中，当消除来自任意代谢物到 crp 基因的反馈边及对 KO 基因影响最大的 10 个代谢反馈基因的反馈边时，基因必需性预测的 F1 分数分别下降了 7.5% 和 13%。最后，我们展示了 CausalFlux 在不同培养基条件下预测数百个基因必需性的应用。总体而言，我们的结果表明，CausalFlux 能够有效利用关于反馈代谢物的信息来预测反应通量趋势及定性（生长/不生长）结果，因此鼓励未来系统建模工作谨慎地将代谢物到基因以及基因到代谢物的双向相互作用纳入模型。

可用性：与 CausalFlux 方法及其基准和应用相关的代码已公开发布于：https://github.com/BIRDSgroup/CausalFlux。

作者摘要：活细胞内的诸多过程，如基因调控或代谢，紧密相关。对这些相互关联过程的建模可以加深对细胞行为的机制理解，并指导细胞代谢输出的工程化。本研究发展了一种将基因调控与代谢整合的创新模型，通过代谢物诱导的基因调控网络因果手术和基因诱导的代谢反应通量约束，融入二者之间的双向反馈。我们称该模型为 CausalFlux，它相较于多数仅捕捉基因到代谢单向反馈（即编码代谢反应控制酶的基因）的现有模型实现了进步。CausalFlux 方法为定量评估基因-代谢物系统中的双向反馈影响提供了独特机会，持续通过将 CausalFlux 的预测结果与仅含单向反馈的已发表模型 TRIMER 进行对比实现。在测试模型中的反应通量预测以及大肠杆菌必需基因鉴定中，CausalFlux 与 TRIMER 的性能定量比较显示，考虑双向反馈能获得更准确且具有生物学意义的预测。CausalFlux 还使我们能够通过在消除特定代谢物到基因反馈边前后的预测表现比较，定量分析双向反馈的效应。总体而言，我们的研究结果强调了将基因调控与代谢作为细胞内双向互联系统进行建模的重要性，并鼓励后续研究将基因↔代谢物反馈纳入分析。

## Abstract
Predicting cellular behaviors, a central task in systems biology and metabolic engineering, can be enhanced through integrative modeling of processes such as gene regulation and metabolism. Information flow from gene regulation (modeled via a gene regulatory network) to metabolism (modeled via a genome-scale metabolic model) is well-studied, but the reciprocal regulation of genes by metabolites is less explored. We introduce CausalFlux, a method that models bidirectional feedback between genes and metabolites, in order to predict steady-state reaction fluxes under wild-type (WT) or perturbed (e.g., gene knockout/KO) conditions. CausalFlux does so by iteratively performing causal surgery on a Bayesian gene regulatory network and constraint-based analysis of a coupled metabolic model. CausalFlux enabled us to assess the impact of two-way feedback in several testbed models and real-world biological systems by comparing its predictions to those of TRIMER, a state-of-the-art model of gene-to-metabolite one-way feedback. Incorporating bidirectional feedback, as in CausalFlux, improved the Spearman correlation between actual and predicted fluxes in 92% of the 39 distinct simulation conditions relative to TRIMER. For predicting growth/no-growth phenotype following single-gene KOs in E. coli, CausalFlux achieved a balanced accuracy of 0.79 in identifying essential genes, and TRIMER achieved 0.71 for the same task, again highlighting the importance of modeling two-way feedback. In ablation studies that further dissect the role of specific metabolite[-&gt;]gene feedback edges in E. coli, the F1 scores of gene essentiality predictions decreased by 7.5% and 13% upon ablation of feedback edges from any metabolite to the crp gene and the 10 metabolic feedback genes with the highest influence on the KO genes, respectively. Finally, we highlight the application of CausalFlux to predict the essentiality of several hundred genes under different media conditions. Overall, our findings show that CausalFlux can crucially utilize information on feedback metabolites to predict trends in reaction fluxes and qualitative (growth/no-growth) outcomes; thereby encouraging future systems modeling efforts to carefully incorporate not only gene-to-metabolite but also metabolite-to-gene interactions.

AvailabilityCode pertaining to the CausalFlux method, and its benchmarking and application is publicly available at: https://github.com/BIRDSgroup/CausalFlux.

Author summaryThe myriad processes within a living cell, such as gene regulation or metabolism, are tightly interconnected. Modeling these interconnected processes can offer a deeper mechanistic understanding of cellular behaviors, as well as guide efforts that engineer the metabolic output of a cell. In this work, we develop a novel integrated model of gene regulation and metabolism that incorporates bidirectional feedback between these two processes, via the concept of metabolite-induced causal surgery on a gene regulatory network and gene-induced constraints on the fluxes of metabolic reactions. Our model, which we call CausalFlux, represents an advance over most existing models that capture just the one-way gene-to-metabolism feedback (i.e., genes coding for enzymes that control metabolic reactions). Our CausalFlux methodology opens up an unique opportunity to quantify the impact of two-way feedback in gene-metabolite systems, via comparison of CausalFluxs predictions to those of TRIMER, a published model incorporating one-way feedback alone. For predicting reaction fluxes in testbed models and essential genes in E. coli, quantitative comparison of the performance of CausalFlux vs. TRIMER showed that accounting for two-way feedback leads to more accurate and biologically meaningful predictions. CausalFlux also enabled us to quantify the effect of two-way feedback by comparing prediction performance before and after ablation of certain feedback edges from metabolites to genes. Overall, our findings highlight the importance of modeling gene regulation and metabolism as two-way interconnected systems within a living cell, and encourage future works to incorporate gene{leftrightarrow}metabolite feedback into their analyses.

---

## 论文详细总结（自动生成）

# 论文总结：利用 CausalFlux 方法对基因–代谢物系统中的双向反馈进行建模与解析

---

## 一、研究核心问题与背景

- **研究动机**  
  当前系统生物学与代谢工程中，整合基因调控网络（GRN）与全基因组尺度代谢模型（GSMM）被视为理解细胞行为的重要途径。  
  然而：
  - 绝大多数模型仅考虑基因对代谢（gene → metabolism）的**单向调控**；
  - **代谢物对基因调控（metabolite → gene）** 的反向反馈研究极少。
- **问题定义**  
  如何系统、可计算地模拟**基因与代谢物之间的双向反馈机制**，从而更准确预测基因敲除后的代谢通量与细胞表型（如生长/不生长）。
- **研究意义**  
  准确建模双向反馈有助于：
  - 提升基因敲除对代谢稳态的预测精度；
  - 揭示基因调控–代谢交互的因果结构；
  - 推动代谢工程与合成生物学的模型化设计。

---

## 二、方法论：CausalFlux 框架

### 1. 核心思想
提出 **CausalFlux**：一种整合贝叶斯基因调控网络与约束代谢模型的迭代式框架，通过“**因果手术（causal surgery）**”实现代谢物→基因反馈的建模。

- 双向耦合路径：
  - **基因→代谢**：由 GPR 规则（Gene–Protein–Reaction）定义；
  - **代谢→基因**：通过“代谢物活化/抑制基因”的反馈边建模。
- 目标：在野生型或基因敲除（KO）条件下预测稳态反应通量。

### 2. 技术流程（算法流程文字描述）

算法分为两个阶段：初始化和迭代整合。

#### （1）初始化阶段
- 利用 **bnlearn** 学习贝叶斯 GRN 结构与参数；
- 对 KO 基因执行**因果手术**（切断父节点边、固定状态为失活 do(A=0)）；
- 在 GSMM 中为反馈代谢物添加 **sink reactions**；
- 执行 Flux Variability Analysis (FVA)，计算初始最小/最大通量边界。

#### （2）迭代整合阶段
每轮迭代包含：
1. 对由活跃代谢物驱动的基因进行 **因果干预**（do 操作）；
2. 通过贝叶斯推理计算基因激活概率 \( P_G \)；
3. 根据 GPR 规则计算反应概率 \( P_R \)；
4. 修正各反应通量上下界：
   \[
   v_{lb,k} = v_{min,k}^0 \times P_{R,k}, \quad v_{ub,k} = v_{max,k}^0 \times P_{R,k}
   \]
5. 对更新后的 GSMM 执行 FBA 与 FVA；
6. 判断反馈代谢物是否处于活跃状态（binarization），若与上轮相同则收敛。

#### （3）收敛与输出
- 若连续两轮活跃代谢物集 \( A^f_b \) 无变化，认为收敛；
- 输出三种预测：FBA、FVA_min、FVA_max，其中 FVA_max 在实验中表现最佳。

---

## 三、实验设计与对比框架

### 1. 实验数据与场景
- **三类模型场景（共 39 组模拟）**：  
  三个测试平台模型（TM1, TM2, TM3）× 不同基因敲除 × 3 种营养交换速率（3.2, 320, 3200 mM/s）；
  用 ODE 动力学仿真生成稳态通量作为 “ground truth”。
- **真实生物数据：**  
  - *E. coli* 数据集（798 个基因单敲除实验，使用 Keio collection 实测生长表型）；
  - 对比不同培养基（LB、M9、TSB）下的必需基因；
  - 旧版本数据集：rFBA、PROM（15 个基因 × 100 种培养基条件）。

### 2. 对比模型
- **TRIMER**：仅建模单向反馈（state-of-the-art 基线）。  
- **GIMME**、**PROM**、**rFBA**：其它约束整合或布尔调控方法。  
- **随机分类器**：基线用于定义最大/最小性能。

### 3. 测试指标
- Spearman 相关系数（ρ）：反应通量预测精度；
- F1-score、平衡准确率（Balanced Accuracy）：基因必需性（growth/no-growth）；
- 通过消融实验评估代谢物→基因反馈的重要性。

---

## 四、资源与算力说明

- 论文**未提供具体算力信息**（如 GPU/CPU 类型、内存或运行时间）。
- 实验所用方法（bnlearn、COBRA Toolbox）均为 CPU 计算型，属于代谢约束分析与贝叶斯推理任务，计算量中等。
- 可复现资源：CausalFlux 开源代码（GitHub: [BIRDSgroup/CausalFlux](https://github.com/BIRDSgroup/CausalFlux)）。

---

## 五、实验数量与充分性

- **总体实验覆盖度极广：**
  - **测试模型仿真：** 39 个场景 × 多通量预测（FBA/FVA_min/FVA_max）。
  - **E. coli 实验：** 798 个单基因 KO × 3 培养基条件。
  - **Ablation 消融实验：** 针对 crp、fur、cra 等高影响反馈基因 + top10 / top40 集合；
  - **外部 benchmark 比较：** PROM / rFBA 100 种培养基 × 15 个基因，共 1500 数据点。
- 结论跨越**合成测试系统 + 实际代谢网络**，设计体系完整，数据充分，可验证性强。

---

## 六、主要结论与发现

1. **性能提升显著：**
   - 在 39 个测试条件中，CausalFlux（FVA_max 变体）在 92% 情况下优于 TRIMER；
   - 通量预测相关度 ρ 最大提高至 0.9；
   - 生物质反应通量预测相关度 0.80，优于 TRIMER 的 0.65。
2. **基因必需性预测更准确：**
   - *E. coli* 单基因 KO：平衡准确率 0.79（TRIMER 为 0.71），F1 提升显著；
   - 预测到 29/47 个实测必需基因。
3. **迭代反馈促进收敛和性能提升：**
   - 多轮反馈迭代可系统改善预测结果；
   - 去除反馈（0次迭代）时精度显著下降。
4. **消融研究揭示反馈关键性：**
   - 去除代谢物→crp 的反馈，F1下降约 7.5%；去除 top10 反馈基因，下降 13%；
   - 多数误判基因均为这些代谢反馈基因的 1-hop 邻域。
5. **外部 benchmark（PROM/rFBA）验证稳定：**
   - 在 100 个培养基中，CausalFlux 在 56% 情况下优于 rFBA；
   - 与 PROM 表现相当，特异性更高（false positive 更少）。
6. **多培养基环境预测：**
   - 在最小培养基 M9 中预测到最多必需基因（133 个），符合营养匮乏的生理预期。

---

## 七、优点与创新亮点

- **算法创新性：**
  - 引入“因果手术”机制，使代谢物—基因反馈可被贝叶斯网络显式干预；
  - 首次在系统层面实现 gene ↔ metabolite 双向建模。
- **可解释性增强：**
  - 通过因果推断支持反馈机制的可视化与生理解释；
  - 消融实验验证机制的功能性重要性。
- **预测全面性：**
  - 无需 KO 特异性转录组数据即可预测通量与表型；
  - 模型自适应不同培养条件。
- **复现性强：**
  - 所有代码与模型公开，可扩展至其他微生物（如 *B. subtilis*、酵母等）。

---

## 八、不足与局限

- **定量预测仍有限：**
  - CausalFlux 为定性或半定量预测，未包含动力学参数；
  - 无法刻画通量的动态变化，仅得稳态信息。
- **多基因扰动未覆盖：**
  - 仅模拟单基因 KO，未扩展到基因组合敲除。
- **算力与复杂度未披露：**
  - 缺少计算成本与时间评估；
  - 贝叶斯网在全基因组尺度下可能存在扩展性挑战。
- **反馈数据依赖**：
  - 代谢物→基因反馈边的生物学知识有限，来源依赖手工整理的 77 条；
  - 模型结果可能受反馈网络不完整的影响。

---

**（完）**
