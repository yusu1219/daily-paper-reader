---
title: Active Learning for Budget-Constrained TCR--pMHC Wet-Lab Validation
title_zh: 预算受限条件下用于 TCR–pMHC 湿实验验证的主动学习
authors: "Mazur, K., Piotrowska, M., Kowalski, J."
date: 2026-04-17
pdf: "https://www.biorxiv.org/content/10.64898/2026.04.14.718510v1.full.pdf"
tags: ["query:gentcr"]
score: 8.0
evidence: 用于TCR-pMHC湿实验验证和模型优化的主动学习
tldr: 本文针对TCR–pMHC结合验证成本高昂的问题，提出一种预算约束下的主动学习方法UDAL，通过结合基于不确定性的MC Dropout和特征空间多样性选择，显著提高模型性能，减少湿实验验证的资源消耗。
source: biorxiv
selection_source: fresh_fetch
figures_json: "[{\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-04-14-718510-v1/fig-001.webp\", \"caption\": \"TABLE II RESULTS AFTER B = 5,000 QUERIED LABELS. COMPARED AGAINST RANDOM BASELINE. ↑: HIGHER IS BETTER; ↓: LOWER IS BETTER.\", \"page\": 3, \"index\": 1, \"width\": 504, \"height\": 292}]"
motivation: 湿实验验证昂贵且耗时，需设计高效的主动学习方案以最大化模型改进。
method: 采用UDAL策略，将不确定性评估与多样性选择相结合，在特征编码空间中进行批量样本获取。
result: "在VDJdb–IEDB数据集上，UDAL以较少的标签数量达到与随机采样三倍数据相当的性能，并提升AUPRC达16.7%。"
conclusion: 研究表明，合理设计的主动学习策略可显著降低建立可靠TCR特异性模型的实验成本。
---

## 摘要
TCR–pMHC 结合假设的湿实验验证是 T 细胞治疗发现过程中的速率限制步骤：单次结合测定实验可能耗费数千美元并需要数周的周期，而计算模型每次运行会生成数千个候选配对。我们将此问题表述为一个\emph{基于样本池的主动学习}问题：在固定标注预算 $B$ 的条件下，应该将哪些未标注配对送去测定，以最大程度提升预测模型的性能，从而指导下一轮筛选？我们提出了 \emph{UDAL}（Uncertainty–Diversity Active Learning，不确定性–多样性主动学习）方法，一种批量数据获取策略，通过 MC Dropout 的 BALD 不确定性估计与编码器特征空间中的贪婪核心集多样性选择相结合。在 curated 的 VDJdb–IEDB 基准上，在表位留出和距离敏感协议下进行评估时，UDAL 在仅查询 5,000 个标签的情况下即可达到 AUPRC 0.487，与使用三倍随机采样标签训练的模型性能相当。在预算为 2,000 个标签的条件下，UDAL 的 AUPRC 较随机采样提升 16.7\%，直接减少了浪费的测定槽位。这些结果表明，基于原理的主动查询策略能够显著降低构建可靠 TCR 特异性模型的湿实验成本。

## Abstract
Wet-lab validation of TCR--pMHC binding hypotheses is the rate-limiting step in T-cell therapy discovery: a single binding assay round can cost thousands of dollars and weeks of turnaround time, yet computational models generate thousands of candidate pairs per run. We frame this as a \emph{pool-based active learning} problem: given a fixed annotation budget $B$, which unlabeled pairs should be sent to the assay to maximally improve a predictive model that will guide the next screening round? We introduce \emph{UDAL} (Uncertainty--Diversity Active Learning), a batch acquisition strategy that combines BALD-based uncertainty estimation via MC Dropout with greedy core-set diversity selection in the encoder feature space. Evaluated on a curated VDJdb--IEDB benchmark under epitope-held-out and distance-aware protocols, UDAL achieves AUPRC 0.487 with only 5{,}000 queried labels---matching the performance of a model trained on 3$\times$ more randomly sampled labels. At a budget of 2{,}000 labels, UDAL improves AUPRC by 16.7\% over random acquisition, translating directly to fewer wasted assay slots. These results demonstrate that principled active query strategies can substantially reduce the wet-lab cost of building reliable TCR specificity models.

---

## 论文详细总结（自动生成）

# 论文总结：预算受限条件下用于 TCR–pMHC 湿实验验证的主动学习（UDAL）

---

## 一、核心问题与研究背景

- **研究主题**：本文针对 T 细胞受体（TCR）与肽–主要组织相容复合体（pMHC）结合预测过程中的高昂湿实验验证成本问题，提出预算受限条件下的主动学习策略。  
- **问题背景**：  
  - 在 T 细胞治疗和新抗原筛选任务中，TCR–pMHC 结合预测需要通过湿实验（如 ELISA、四聚体染色、共培养功能实验）确认。  
  - 每次湿实验验证周期长、费用高（数千美元），而计算模型能生成成千上万个候选配对。
  - 常规监督学习假设已有足够且无偏的标签数据，但现实中标注数量有限且代价高昂。  
- **研究目标**：  
  - 在总标注预算 \( B \) 受限的情况下，确定哪些未标注样本最值得进行实验验证。  
  - 通过引入主动学习机制，提高模型性能、降低实验成本。

---

## 二、方法论：UDAL 主动学习策略

- **总体思路**：在有限标注预算下，通过结合不确定性采样与多样性选择，最大化每一批查询数据的模型改进增益。  
- **核心组成**：
  1. **不确定性估计（Uncertainty）** — 使用 *BALD (Bayesian Active Learning by Disagreement)* 指标评估模型 epistemic 不确定性：
     \[
     a_\text{BALD}(x) = H(\bar{p}(x)) - \frac{1}{M}\sum_{m=1}^M H(\hat{p}^{(m)}(x))
     \]
     其中 \( \hat{p}^{(m)}(x) \) 为 MC Dropout 下的第 \( m \) 次预测。
     - 高 BALD 值意味着模型对样本预测存在较大分歧，代表值得标注的样本。
  2. **多样性选择（Diversity）** — 在嵌入特征空间（由 ESM-2 编码器产生）中选取代表性样本，避免标注冗余：
     \[
     e_d(x) = \min_{x'\in L_t} \|\varphi(x) - \varphi(x')\|_2
     \]
     并采用贪婪核心集（Greedy Core-Set）算法保证查询样本覆盖最大化。
  3. **加权组合策略（UDAL）**：
     \[
     a_\text{UDAL}(x) = \alpha \, e_{a_\text{BALD}}(x) + (1-\alpha) \, e_d(x)
     \]
     - 权重 \(\alpha = 0.6\)，在不确定性与多样性之间达到平衡。  
- **算法流程（简述）**：
  1. 以小规模种子标签集 \( L_0 \) 训练初始模型；
  2. 在每轮中计算未标注样本的不确定性与多样性分数；
  3. 按 \( a_\text{UDAL} \) 综合得分选取批量样本查询；
  4. 获取真实标签（湿实验结果模拟为 “oracle”），更新训练集重新训练模型；
  5. 重复 \( R \) 轮直至预算耗尽。

---

## 三、实验设计

- **数据集与场景**：  
  - 使用 *VDJdb–IEDB* 组合基准数据集（HLA-A*02:01，人类 TCR αβ 配对）。
  - 按三种划分方式测试：
    1. **Random**：随机划分；
    2. **Epitope-Held-Out (EHO)**：表位留出，模拟分布外测试；
    3. **Distance-Aware (DA)**：距离感知划分，控制嵌入空间差异。  
- **基准协议**：
  - 种子集 \( L_0 = 1000 \)；
  - 查询批次 \( b = 1000 \)，共 \( R=5 \) 轮，总预算 \( B=5000 \)；
  - 每轮后重新训练模型，并在固定测试集上评估 AUPRC、AUROC、ECE（校准误差）及 Label Efficiency。  
- **对比方法**：
  1. Random（随机采样）  
  2. BALD-only（纯不确定性采样）  
  3. CoreSet-only（纯多样性采样）  
  4. UDAL（本研究方法）  

---

## 四、资源与算力

- **论文未明确说明**所使用的算力资源或硬件配置（未提及 GPU 型号、数量或训练时间）。  
- 模型使用 *ESM-2* 编码器与两层 MLP 分类器，但未描述训练规模或参数量。因此无法评估资源成本。

---

## 五、实验数量与充分性

- **实验覆盖**：
  - 主实验：三种数据划分（EHO / DA / Random），各方法对比共 12 组主要数值。
  - **学习曲线**：不同预算标签数量下性能变化（1k–5k 标签）。
  - **消融实验**：对权重参数 α、MC Dropout 次数 M、批量大小 b、距离度量方式等进行系统探究。
  - **分布外分析**：计算 OOD/ID 增益比率并进行统计检验（p-value）。  
- **充分性与公平性**：
  - 所有方法共享相同种子集与模型架构；
  - 实验平均于 5 个随机种子；
  - 评价指标多样、结果稳定，实验设计较公正。  
  → 整体实验量充足且系统完善。

---

## 六、主要结论与发现

- UDAL 方法在预算约束条件下显著提升标签使用效率：
  - 仅 2,000 标签即可超过随机采样 5,000 标签的性能（AUPRC = 0.448 vs. 0.418），约 **2.5× 成本节省**。
  - 在完整预算 \( B=5000 \) 条件下，UDAL 达到 AUPRC = 0.487，接近全监督上限（0.491）。
- 在分布外场景（表位留出、距离感知）中，UDAL 相较随机采样提升达 **+16.7%**。
- 多样性采样在分布漂移下作用更大，比纯不确定性采样更稳健。
- 提出新的标签效率指标 LE（AUPRC 每 1000 标签提升量），能直接映射到实验节约比例。
- 模拟预算节省约 **$150,000**（假设每次实验 $50 成本）。

---

## 七、优点与亮点

- **创新方法论**：
  - 在生物分子主动学习领域首次结合 *BALD + CoreSet* 于 TCR–pMHC 任务；
  - 提出了统一的预算约束公式与算法框架。  
- **评估体系完善**：
  - 同时考虑不确定性、多样性、分布外泛化及实验经济性；
  - 引入可解释的“标签效率”指标，转换为实际成本节约。  
- **实验可靠**：
  - 多种协议、种子多次采样、AUPRC–学习曲线–消融分析并重；
  - 对分布漂移与信息增益进行了定量验证。  
- **实用导向**：
  - 明确指标与湿实验预算挂钩，适合在药物发现与免疫识别实际流程中应用。

---

## 八、不足与局限

- **算力与可复现性**：未说明硬件环境，难以估算计算负担。  
- **模拟验证**：使用静态数据集模拟“实验 oracle”，未考虑真实湿实验的不确定性（如批次效应、假阴性率）。  
- **数据动态性**：假设未标注样本池固定，实际研究中 TCR 库动态扩展，需要在线型主动学习方法。  
- **成本模型简化**：默认标注成本相同，未区分阳性/阴性样本的实验代价差异。  
- **分布偏差风险**：主动学习可能聚焦高不确定性或远离种子集的样本，从而引入新的分布偏移。  

---

**（完）**
