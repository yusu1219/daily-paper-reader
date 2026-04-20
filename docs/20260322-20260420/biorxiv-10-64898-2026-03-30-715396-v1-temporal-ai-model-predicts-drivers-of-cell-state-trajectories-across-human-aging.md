---
title: Temporal AI model predicts drivers of cell state trajectories across human aging
title_zh: 时间序列人工智能模型预测人类衰老过程中细胞状态轨迹的驱动因素
authors: "Gomez Ortega, J., Nadadur, R. D., Kunitomi, A., Kothen-Hill, S., Wagner, J. U. G., Kurtoglu, S. D., Kim, B., Reid, M. M., Lu, T., Washizu, K., Zanders, L., Chen, H., Zhang, Y., Ancheta, S., Lichtarge, S., Johnson, W. A., Thompson, C., Phan, D. M., Combes, A. J., Yang, A. C., Tadimeti, N., Dimmeler, S., Yamanaka, S., Alexanian, M., Theodoris, C. V."
date: 2026-04-01
pdf: "https://www.biorxiv.org/content/10.64898/2026.03.30.715396v1.full.pdf"
tags: ["query:virtcell"]
score: 10.0
evidence: 时间AI模型预测衰老过程中扰动对细胞状态的影响
tldr: 本研究针对当前AI模型难以捕捉细胞随时间变化问题，提出了时间序列AI模型MaxToki。该模型基于近万亿基因数据训练，能生成和预测人类衰老过程中的细胞状态轨迹，并发现多种经实验验证的调控衰老相关基因，为开发抗衰治疗提供新方向。
source: biorxiv
selection_source: fresh_fetch
figures_json: "[{\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-03-30-715396-v1/fig-001.webp\", \"caption\": \"Fig. 4. Interpretability analysis revealed context-specific specialization of attention heads and higher attention to central regulators. (A) Aging timelapse prediction for held-out cell types was significantly damaged by shuffling gene order within the rank value encoding, indicating that relative gene expression levels in each cell state\", \"page\": 11, \"index\": 1, \"width\": 976, \"height\": 1264}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-03-30-715396-v1/fig-002.webp\", \"caption\": \"Fig. 6. In silico perturbation predicted pro-aging perturbations that were experimentally verified in cardiac cell types. (A) Predicted impact of in silico inhibition vs. slope of expression change across human aging for genes in cardiac fibroblasts. (B) Concordant genes whose inhibition was predicted to be rejuvenating were upregulated across\", \"page\": 15, \"index\": 2, \"width\": 981, \"height\": 1270}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-03-30-715396-v1/fig-003.webp\", \"caption\": \"Fig. 2. Generated cell states were consistent with the prompted cell context. (A) Cells generated in response to a prompted contextual trajectory were annotated by an external cell type classifier model with 82% concordance with annotations of ground truth cells of that cell type (n=87,083). (B) Generated and ground-truth cells of the same cell\", \"page\": 7, \"index\": 3, \"width\": 979, \"height\": 1256}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-03-30-715396-v1/fig-004.webp\", \"caption\": \"Fig. 5. MaxToki inferred age acceleration of cell states in age-related conditions. (A) Inferred age acceleration of disease cell states vs. age-matched controls in donors exposed to heavy smoking (lung mucous secretory epithelial cells) or affected by pulmonary fibrosis (lung fibroblasts) (n=5000). (B) Matched donor ages for disease vs. control query cells used for analysis shown in (A). Lines indicate comparison subgroups. (C) Inferred age acceleration of disease cell states vs. age-matched controls in patients affected by Alzheimer dementia, mild cognitive impairment, or resilient patients who have the same neuropathology as Alzheimer patients with no cognitive impairment (dataset 1: microglia, n=5000; dataset 2: homeostatic microglia, n=2507). (D) Matched donor ages for\", \"page\": 13, \"index\": 4, \"width\": 868, \"height\": 545}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-03-30-715396-v1/fig-005.webp\", \"caption\": \"Fig. 1. MaxToki learned to generate cell states and predict the timelapse needed to induce cell states across long trajectories of human aging. (A) Two-stage training strategy of MaxToki. The model is trained in total on nearly 1 trillion gene tokens (non-trivial tokens, excluding non-expressed genes). MSE=mean-squared error,\", \"page\": 4, \"index\": 5, \"width\": 974, \"height\": 1276}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-03-30-715396-v1/fig-006.webp\", \"caption\": \"Fig. 3. MaxToki generated cell states capturing non-monotic gene activation in held-out inflection intervals within short timelapse trajectories. (A) Diagram of held-out inflection intervals across partial reprogramming pseudotime trajectories in the indicated cell types. The plots indicate the proportion of cells at each point in pseudotime representing cells annotated by cell markers for each stage of partial reprogramming. While the proportion of cells in each stage may appear monotonic, gene expression levels may change non-monotonically within the held-out intervals, as indicated in (D). (B) Pseudo-timelapse prediction for held-out intervals compared to baseline of predicting most common pseudo-timelapse for that cell type. *p<0.05, Wilcoxon rank sums (n=25,000). (C) Correlation of predicted vs. ground truth pseudotime for each cell type in held-out intervals (n=100). (D) Ground truth differential expression of top 100 upregulated or downregulated genes by rank within generated (top) or ground truth (bottom) cells from inflection intervals 2-3 in cytotoxic T lymphocytes. (E) Generated vs. ground truth differential ranking of genes vs. interval 2-3 in cytotoxic T lymphocytes (n=4463). (F) Ground truth differential expression vs.\", \"page\": 9, \"index\": 6, \"width\": 976, \"height\": 1045}]"
motivation: 现有AI模型无法充分捕捉细胞状态在衰老等长时间过程中的动态变化。
method: 研究开发了名为MaxToki的时间序列AI模型，使用近万亿基因数据训练以预测和生成细胞状态的时间变化。
result: MaxToki能够泛化至未见过的细胞轨迹，并准确预测经实验证实的调节衰老的目标基因。
conclusion: MaxToki展示了时间建模在加速发现调控细胞衰老干预靶点方面的潜力。
---

## 摘要
基础性的人工智能模型近年来在预测扰动对细胞状态影响方面展现出潜力。然而，现有模型通常一次只考虑一个细胞状态，限制了其学习细胞反应随时间展开方式的能力，尤其是在涉及衰老相关疾病等长时间轨迹的情况下。在此，我们开发了一种时间序列人工智能模型 MaxToki，该模型在包含近一万亿基因标记的数据上进行训练，其中涵盖了跨越人类生命周期的细胞状态轨迹，用以生成跨越人类衰老长时间序列的细胞状态。MaxToki 通过上下文学习推广至未见过的轨迹，并预测了新的可调控年龄的靶点。实验验证表明，这些靶点可在体内影响与年龄相关的基因程序及功能性衰退。MaxToki 代表了一种有前景的时间建模策略，可加速发现用于编程治疗性细胞轨迹的干预措施。

## Abstract
Foundational AI models have recently shown promise for predicting the impact of perturbations on cell states. However, current models typically consider only one cell state at a time, limiting their ability to learn how cellular responses unfold over time, particularly across long trajectories such as diseases of aging. Here, we develop a temporal AI model, MaxToki, trained on nearly 1 trillion gene tokens including cell state trajectories across the human lifespan to generate cell states across long timelapses of human aging. MaxToki generalized to unseen trajectories through in-context learning and predicted novel age-modulating targets that were experimentally verified to influence age-related gene programs and functional decline in vivo. MaxToki represents a promising strategy for temporal modeling to accelerate the discovery of interventions for programming therapeutic cellular trajectories.

---

## 论文详细总结（自动生成）

# 时间序列人工智能模型 MaxToki 综述与分析  

---

## 一、研究动机与背景

- **核心问题**：现有的人工智能模型（例如 Geneformer、scGPT、scFoundation 等）在预测基因网络动态方面取得进展，但主要将细胞状态视为静态"快照"。这限制了模型捕捉细胞随时间变化（如衰老、疾病进程）的能力。  
- **研究目标**：建立一个能够模拟长期细胞状态变化（cell state trajectory）的模型，用于预测干预措施对细胞命运的长期影响。  
- **意义**：在人类衰老研究中，无法直接随时间追踪同一人的细胞，因此需要构建**人口基于时间序列的推断模型**。能预测干预手段如何改变细胞衰老轨迹，有助于发现延缓衰退的新药靶。

---

## 二、方法论：MaxToki 模型的核心思想与技术细节

### 1. 模型总体设计

- **模型类型**：基于 Transformer 解码器的生成式时间序列模型。  
- **核心任务**：  
  - 任务1：预测两种细胞状态之间的时间间隔（timelapse）。  
  - 任务2：生成给定时间延迟后应出现的目标细胞状态。  

- **训练流程（两阶段）**：  
  1. **阶段一（单细胞预训练）**：学习生成单细胞转录组（使用 Rank Value Encoding 方法，将基因表达值转化为相对排序序列）。  
  2. **阶段二（时间序列训练）**：输入多个细胞状态序列，学习细胞随时间变化规律，并通过连续数值化的时间 token 进行 self-supervised 学习。  

### 2. 数据编码策略

- **Rank Value Encoding**：对每个细胞的基因按表达值排序，忽略绝对数量值，减少测序噪声影响。  
- **Temporal Encoding**：多个细胞状态串联，中间插入时间间隔 token，并在输入序列中加上特殊标识（如 BOS、EOS、BOQ、EOQ）。  
- **连续数值化 token（Continuous Numerical Tokenization）**：利用连续值编码时间，与传统离散标签相比，更能捕捉衰老的连续变化。

### 3. 关键技术模块

- **RoPE scaling**：扩展模型的上下文窗口至 16,384，以容纳多细胞时间序列。  
- **GPU 加速与优化**：采用 NVIDIA BioNeMo、Megatron-LM、Transformer Engine 堆栈；使用 FlashAttention-2、混合精度（bf16）训练、大规模 key-value 缓存。  
- **损失函数**：  
  - Cell 生成任务使用 **交叉熵（CE）损失**；  
  - 时间预测任务使用 **均方误差（MSE）损失**，鼓励模型学习时间连续性。  
- **推理框架**：采用 Megatron-Core 的 DynamicInferenceContext 管理缓存与序列打包，提高生成速度（提升达 400 倍）。

---

## 三、实验设计与数据来源

### 1. 数据集构成

| 阶段 | 数据集名称 | 内容 | 数量 |
|------|--------------|------|------|
| 第一阶段 | **Genecorpus-175M** | 来自约10,795个公开数据集的人类单细胞转录组（去除癌细胞和细胞系） | 约1.75亿细胞 |
| 第二阶段 | **Genecorpus-Aging-22M** | 3805名正常人、覆盖从出生到90岁、22百万单细胞 | 约1亿时间序列样本 |
| 短时再程序化实验 | OSKM 重编程（T细胞、成纤维细胞、内皮细胞） | 4名供体 / 每类型 |
| 疾病分析 | 吸烟、肺纤维化、阿尔茨海默病等 | 外部单细胞数据 |

### 2. 评估场景与基准方法

- **基线模型**：  
  - 线性模型（SGDRegressor）。  
  - 基于统计假设（"预测细胞为该类型最常见年龄"的规则）。  
- **评估维度**：  
  - 对比 timelapse 预测误差与相关系数。  
  - 验证生成的细胞与真实细胞类型、年龄的匹配度。  
  - 通过外部模型 Geneformer 评估嵌入空间相似性。  
- **消融实验**：包括“bag of genes”（随机打乱基因顺序）和输入遮掩实验，验证模型依赖上下文与基因顺序的有效性。

---

## 四、资源与算力配置

- **217M 参数模型**：使用 24× NVIDIA H100 80GB GPU，fp32 精度。  
- **1B 参数模型**：使用 32× NVIDIA H200 141GB GPU，bf16 混合精度。  
- **优化结果**：通过 Transformer Engine 与 FlashAttention-2 提升约 5 倍训练吞吐、4 倍批次规模；推理速度提高 400 倍。  
- **训练数据规模**：近 **1万亿基因 token**。  
- **推理与评估**：使用 NVIDIA Megatron-Core 框架进行高速动态缓存推理。  
- **训练时长**：文中未明确给出各阶段持续时间。

---

## 五、实验数量与充分性分析

- **主要实验类别**：  
  1. **模型预训练性能刻度实验**（不同参数规模下的标度规律）。  
  2. **长期衰老轨迹预测**（横跨出生至90岁、不同细胞类型与性别）。  
  3. **短期再编程轨迹实验**（OSKM 重编程的非单调转录变化验证）。  
  4. **泛化验证**（对未见年龄、未见细胞类型的预测）。  
  5. **模型解释性实验**（注意力权重分析与特征专化）。  
  6. **疾病年龄加速推断**（吸烟、肺纤维化、阿尔茨海默与认知韧性群体）。  
  7. **in silico 干扰预测与实验验证**（细胞与小鼠体内验证）。

- **实验充分性**：覆盖从计算到生物实验的多层验证（AI 模拟 → 细胞培养 → 动物模型），技术与生物层面均较全面。
- **公平性与客观性**：实验使用未见数据验证泛化；但部分疾病样本量较小（如肺纤维化 n≈3），存在统计限制。

---

## 六、主要结论与发现

1. **模型能力**  
   - MaxToki 能基于上下文学习预测未见年龄与未见细胞类型的时间变化，Timelapse预测的相关系数达 0.77–0.85。  
   - 生成细胞的类型正确率达 82%，并能重建单细胞分辨率。  

2. **生物学发现**  
   - 推断出多种疾病状态存在“加速衰老”信号：  
     - 吸烟肺上皮细胞 ≈ +5年；  
     - 肺纤维化成纤维细胞 ≈ +15年；  
     - 阿尔茨海默患者微胶质细胞 ≈ +3年。  
   - 模型预测并实验验证**五个促衰老基因**（ATF3、EYA4、NR4A3、NXN、P4HA1、RASGEF1B），其过表达可在 iPSC 心肌细胞中诱发功能下降与节律异常。  
   - 其中 P4HA1、RASGEF1B 在体内小鼠实验中引起心脏收缩功能下降，验证模型预测的真实性。  

3. **解释性结果**  
   - 注意力机制自监督学习到显著聚焦于**转录因子（TF）**，据信为细胞状态变化的关键驱动。  
   - 不同注意力头展示出细胞类型特异性，说明模型能够适应上下文差异。

---

## 七、方法亮点与创新性

- **时间序列化学习框架**：首次将 Transformer 应用于细胞状态的时序建模与生成。  
- **连续时间 token 化策略**：突破了传统年龄分类的离散限制，实现跨年龄段平滑泛化。  
- **自监督 + 上下文学习**：无需显式标签即可学习年龄与类型信息。  
- **GPU工程突破**：FlashAttention-2 与 Transformer Engine 的结合显著提升了训练与推理效率。  
- **从计算到实验的闭环验证**：预测结果经细胞功能和动物实验双重验证，形成 AI-实验协同体系。  

---

## 八、不足与局限

- **数据偏差**：  
  - 由于使用公共数据整合，样本来源异质性较高，存在批次效应和平台差异。  
  - 疾病模型样本量偏小，尤其是肺纤维化与吸烟组，仅数名供体。  
- **时间分辨率限制**：模型虽然覆盖0到90岁，但真实时间轨迹非同一个体连续测量，属于拟时间（pseudo-timelapse）。  
- **计算资源门槛**：1B参数模型需要高端GPU阵列，对一般研究者复现成本极高。  
- **生物验证局限**：实验主要集中在心脏与微胶质细胞，其他组织验证尚不充分。  
- **理论扩展空间**：目前模型未显式建模因果关系，仅在统计层面学习趋势。

---

**（完）**
