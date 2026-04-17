---
title: Deciphering antigen-driven T cell responses through vectorized TCRdist sequence neighborhood quantification
title_zh: 通过向量化 TCRdist 序列邻域量化解析抗原驱动的 T 细胞反应
authors: "Valkiers, S., Mayer-Blackwell, K., Yeh, A. C., Van Deuren, V. M. L., Fiore-Gartland, A., Hill, G., Laukens, K., Meysman, P., Bradley, P."
date: 2026-04-14
pdf: "https://www.biorxiv.org/content/10.64898/2026.04.10.717405v1.full.pdf"
tags: ["query:gentcr"]
score: 9.0
evidence: 用于TCRdist距离和向量化TCR序列邻域分析的计算框架
tldr: 本文提出一种高效的计算框架，通过向量化的TCRdist序列邻域量化，实现T细胞受体（TCR）相似性快速近似计算与多库规模的富集分析，克服现有方法在区分抗原驱动选择与随机重组偏差上的局限，验证了其在疫苗和病毒感染中识别收敛性T细胞特征的能力。
source: biorxiv
selection_source: fresh_fetch
figures_json: "[{\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-04-10-717405-v1/fig-001.webp\", \"caption\": \"\", \"page\": 19, \"index\": 1, \"width\": 4134, \"height\": 4784}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-04-10-717405-v1/fig-002.webp\", \"caption\": \"\", \"page\": 20, \"index\": 2, \"width\": 2838, \"height\": 1897}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-04-10-717405-v1/fig-003.webp\", \"caption\": \"\", \"page\": 21, \"index\": 3, \"width\": 5906, \"height\": 5118}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-04-10-717405-v1/fig-004.webp\", \"caption\": \"\", \"page\": 22, \"index\": 4, \"width\": 3404, \"height\": 3057}]"
motivation: 当前TCR相似性分析方法难以区分真实的抗原驱动反应与重组偏差且计算耗时。
method: 研究采用固定长度向量嵌入和优化的邻近搜索算法，结合基于洗牌的背景模型进行相似性富集测试。
result: 实验验证该方法能显著检测记忆T细胞中的富集克隆，并识别疫苗及病毒感染的收敛T细胞反应。
conclusion: 该研究提供了一种可扩展且稳健的抗原无关T细胞响应分析方法。
---

## 摘要
T 细胞通过其高度可变的 T 细胞受体（TCR）表达，提供了精确的机制来防御感染和肿瘤。然而，如何解释 TCR 之间的相似性仍然是一个重大挑战。尽管已有高性能的聚类方法存在，但这些方法往往无法区分由抗原驱动的趋同选择与由 V(D)J 重组机制偏差随机产生的模式。此外，在大型受体库中定义序列相似性富集的计算成本极高。为解决这些问题，我们提出了一种高效的计算框架，利用固定长度向量嵌入和高度优化的最近邻搜索，实现对 TCRdist 距离的快速近似，从而可以在多受体库尺度上进行序列相似性富集检测。该框架利用一种基于洗牌的全新背景模型，比合成模型更准确地保留了受体库的重要特征，如 V 基因频率、CDR3 序列长度和生成概率。结合这些工具，我们能够高效且稳健地在大规模数据中识别显著邻居富集（SNE）的 TCR 序列。我们进一步通过在记忆 T 细胞部分发现 SNE 克隆显著富集来验证该方法的有效性，并展示其在识别疫苗接种和病毒感染反应中的趋同 T 细胞特征方面的实用性，为抗原非依赖的 T 细胞反应分析提供了一种可扩展的方法。

## Abstract
T cells provide precise mechanisms to defend the body against infection and malignancies, mediated through the expression of their hypervariable T cell receptors (TCRs). Interpreting similarity between TCRs, however, remains a significant challenge. While performant clustering methods exist, these often fail to distinguish between antigen-driven convergent selection and patterns arising stochastically from biases in the V(D)J recombination mechanism. Moreover, defining enrichment in sequence similarity among large repertoires is computationally taxing. To address these limitations, we present an efficient computational framework for rapid approximation of TCRdist distances using fixed-length vector embeddings and highly optimized nearest neighbor search, allowing sequence similarity enrichment testing at a multi-repertoire-wide scale. This framework leverages a novel shuffling-based background model that preserves important repertoire characteristics such as V gene frequency, CDR3 sequence length and generation probability more accurately than synthetic models. Together, these tools enable the efficient and robust identification of significantly neighbor enriched (SNE) TCR sequences at scale. We validate this approach by showing a significant enrichment of SNE clones in memory T cell fractions and further demonstrate its utility in identifying convergent T cell signatures of response to vaccination and viral infections, providing a scalable approach for antigen-agnostic T cell response profiling.

---

## 论文详细总结（自动生成）

# 论文总结：通过向量化 TCRdist 序列邻域量化解析抗原驱动的 T 细胞反应  
（Deciphering antigen-driven T cell responses through vectorized TCRdist sequence neighborhood quantification）

---

## 一、研究核心问题与整体背景

- **研究动机：**  
  T 细胞受体（TCR）序列的相似性分析是理解免疫反应的关键。然而，TCR 序列多样性极高，且存在由 V(D)J 重组机制引入的偏差，使得区分真实的抗原驱动趋同选择与随机生成的相似模式十分困难。  
  现有聚类和距离度量（如 TCRdist）虽具表现力，但计算量巨大，不适用于多受体库（multi-repertoire）级分析。

- **核心问题：**  
  如何在保证计算效率的前提下，准确识别由抗原反应驱动的趋同性 TCR 序列（即在序列空间中相互相似的克隆体），同时排除随机重组带来的虚假相似性。

- **研究目标：**  
  建立一个高效、可扩展的计算框架，通过**向量化 TCRdist（vecTCRdist）**及**基于洗牌的背景模型**，在大规模受体库中高效检测显著邻居富集（SNE, Significantly Neighbor-Enriched）克隆，从而捕捉抗原驱动的 T 细胞反应特征。

---

## 二、方法论与技术实现

### 1. 核心思想

- 将 TCRdist 序列距离（基于 CDR 区域序列相似性）**转化为固定长度向量表示**；
- 使用**欧式空间搜索（Euclidean nearest neighbor）**快速近似 TCRdist；
- 结合一种保留生物统计特征的**洗牌式（shuffled）背景模型**，检测特定克隆的邻域是否显著富集；
- 通过统计检验（超几何分布 + Bonferroni 校正）筛选显著邻域富集的 TCR。

### 2. 技术流程

1. **特征编码（vecTCRdist embedding）：**
   - 将 CDR1、CDR2、CDR2.5、CDR3 区域各自修剪与统一长度；
   - 利用 BLOSUM62 转换为 TCRdist 距离矩阵，再用多维尺度分析（MDS）将 21×21 氨基酸距离矩阵压缩成 n 维向量；
   - 拼接所有氨基酸向量 → 得到固定长度的 TCR 表示；
   - 欧氏距离近似 TCRdist。

2. **相似性搜索：**
   - 基于 **Faiss 库**（Facebook AI Similarity Search）进行核查；
   - 可使用 **“精确”（flat）** 或 **“近似”（IVF）** 索引；
   - 典型半径设定 \(r=12.5\)（单链）。

3. **背景模型：**
   - 对比三种方案：  
     - *OLGA base*: 传统生成概率模型（偏差明显）。  
     - *OLGA V-CDR3*: 校正 V 基因和 CDR3 长度。  
     - *SHUF V-CDR3*: 利用生物学可行的重组位点重新洗牌序列，保留样本特征（推荐方案）。
   - 构建背景比例可调（1:1 to 1:500），实验表明 >10:1 即稳定。

4. **邻域显著性计算（clustcrdist）：**
   - 使用超几何分布计算观察邻居数量≥k 的概率；
   - Bonferroni 校正抵消多重比较；
   - 得到显著邻居富集的克隆（SNE）。

5. **结果注释：**
   - 使用 **VDJdb 数据库** 注释 SNE 克隆的潜在抗原特异性。

---

## 三、实验设计与评估

### 1. 数据来源与场景

共使用多个高质量公开与自建数据集：

| 数据类型 | 物种 | 内容 | 参考文献 |
|-----------|------|--------|----------|
| 公共库 | 人 | 多组 AIRR 数据 | [10–15] |
| 自建数据 | 鼠 | 分选的 Naive 与 Memory CD4 T cells | 本研究生成 |
| 疫苗数据 | 人 | 黄热病疫苗（YFV）接种前后多时点 | [13] |
| 感染数据 | 人 | SARS-CoV-2 感染患者的纵向 αβ 配对数据 | [10] |
| 生命周期数据 | 人 | 从脐带血至百岁老人样本 | [12] |
| 大型群体数据 | 人 | 含 HLA 分型和 CMV 状态（Emerson cohort, n=666） | [15] |

### 2. Benchmark 与对比方法

- **对比基础模型：** OLGA base vs OLGA V-CDR3 vs SHUF V-CDR3；  
  后者在 V 基因、CDR3 长度及生成概率上对真实分布拟合最优。
- **性能测试：**  
  - 使用 vecTCRdist 与 TCRdist 的皮尔逊相关（ρ≥0.97，7维以上即可稳定）；  
  - 测试 IVF vs flat 索引速度与准确度（99.2% 边捕获、速度提升约7倍）。

---

## 四、计算资源与环境

- **硬件：**  
  CPU: Intel Core i7-10875H (8核16线程)，16 GB 内存；  
  并未使用 GPU。

- **软件栈：**  
  Python 3.9；faiss 1.7.2；scipy、statsmodels、scikit-learn；  
  图形输出使用 matplotlib 与 seaborn。

- **说明：**  
  未提及使用 GPU 加速或大量分布式算力，强调算法本身在 CPU 上即可实现大规模近似计算。

---

## 五、实验丰富性与客观性

- 实验维度广泛：
  1. **算法验证：** vecTCRdist 与 TCRdist 的相关性实验；
  2. **性能测试：** 在 10k–500k 克隆集规模上的时间与准确性评估；
  3. **模型比较：** 背景模型（OLGA vs SHUF）性能对比；
  4. **生物验证：**  
     - 小鼠 Naive vs Memory；  
     - 人类 Naive / EM / CM；  
     - 黄热病疫苗反应；  
     - SARS-CoV-2 感染纵向追踪；  
     - 年龄关联分析（UCB–百岁）；  
     - CMV/EBV 感染群体统计；  
     - HLA 关联测试。
- 实验结果一致、统计检验合理（Mann-Whitney、FDR、Bonferroni 均使用）。
- 充分覆盖了不同生物学层面与多种应用场景，结果重复性良好。

---

## 六、主要结论与发现

1. **vecTCRdist 高效准确：**  
   - 仅需 7 维编码即可与原 TCRdist 保持 ρ>0.97 的距离相关。  
   - IVF 索引在大数据上提供 ~7× 加速。

2. **SHUF 背景模型最逼近真实分布：**  
   - 最好地重现 V 基因比例、CDR3 长度及 Pgen 分布，无需额外选择因子。

3. **生物学验证结果：**
   - 记忆 T 细胞相比初始 T 细胞显著富集 SNE 克隆；
   - YFV 疫苗接种及 SARS-CoV-2 感染中，SNE 克隆体现出**趋同选择特征**；
   - SARS-CoV-2 时期部分 SNE 克隆与 Spike 表位（YLQPRTFLL、SPRWYFYYL）匹配；
   - 年龄进程中，年轻与中年群体 SNE 水平最高，老年后下降；
   - SNE 克隆常富集 CMV、EBV、Influenza A 特异性；
   - SNE 还揭示了新的 HLA 相关 TCR 序列（303 个显著 HLA 关联克隆，其中 148 个为新增）。

---

## 七、优点与创新点

- **算法创新：**
  - 将复杂的 TCRdist 度量映射到可计算的向量空间；
  - 支持多库规模的欧几里得近似检索；
  - 提示性强的洗牌式背景校正。

- **计算性能：**
  - 显著提升速度与可扩展性，无需 GPU；
  - 可灵活调节维度与距离半径，兼容多链数据。

- **生物学解释性：**
  - SNE 检测精确反映抗原驱动收敛；
  - 比单纯克隆扩增分析更能捕捉疫苗/病毒反应。

- **通用性：**
  - 适用单链与配对 αβ TCR；
  - 可用于多种物种与群体数据。

---

## 八、不足与局限

- **距离阈值固定：**  
  r=12.5 可能无法适应所有 TCR 长度或特定表位；
- **单一距离度量：**  
  仅基于 TCRdist，部分特异性可能在其他度量（如 tcrBLOSUM）中表现更好；
- **计算复杂性：**  
  高维向量虽然准确，但>15维显著降低效率；
- **规模偏倚风险：**  
  富集克隆数随库大小增长可能不成比例；
- **实证局限：**  
  多集中于病毒性感染与疫苗刺激，未覆盖自身免疫或肿瘤抗原背景；
- **资源报告不足：**  
  未给出大型数据库在真实 HPC/GPU 环境中的运行时长，缺少性能可重现实验。

---

（完）
