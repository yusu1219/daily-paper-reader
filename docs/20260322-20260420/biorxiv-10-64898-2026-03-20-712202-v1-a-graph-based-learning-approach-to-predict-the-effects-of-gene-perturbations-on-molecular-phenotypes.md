---
title: A graph-based learning approach to predict the effects of gene perturbations on molecular phenotypes
title_zh: 一种基于图的学习方法用于预测基因扰动对分子表型的影响
authors: "Jin, Y., Sverchkov, Y., Sushkova, A., Ohtake, M., Emfinger, C., Craven, M."
date: 2026-03-23
pdf: "https://www.biorxiv.org/content/10.64898/2026.03.20.712202v1.full.pdf"
tags: ["query:virtcell"]
score: 9.0
evidence: 预测基因扰动对分子表型的影响以优先排序敲除实验
tldr: 本文提出一种基于图的机器学习方法，用以预测基因扰动对分子表型的影响。该方法利用已测扰动数据与生物网络特征，能准确预测未测基因的表型效应，优于传统基准，并可指导实验设计，揭示潜在的基因作用机制。
source: biorxiv
selection_source: fresh_fetch
figures_json: "[{\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-03-20-712202-v1/fig-001.webp\", \"caption\": \"Figure 4. Predictive accuracy of learned models trained on individual subgraph feature groups versus models trained on all features. Each panel shows the results for a learning algorithm applied to all four phenotypes.\", \"page\": 6, \"index\": 1, \"width\": 494, \"height\": 316}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-03-20-712202-v1/fig-002.webp\", \"caption\": \"Figure 3. Learning curves for baseline methods and the learning methods. Each panel shows the results for one phenotype. The x-axis shows the fraction of the available training set used and y-axis shows the resulting AUROC values.\", \"page\": 6, \"index\": 2, \"width\": 492, \"height\": 400}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-03-20-712202-v1/fig-003.webp\", \"caption\": \"Figure 2. Predictive accuracy of the four learning algorithms for the four phentoypes. Each panel shows the ROC curves and AUROC values for each learning method on the given phenotype.\", \"page\": 5, \"index\": 3, \"width\": 492, \"height\": 409}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-03-20-712202-v1/fig-004.webp\", \"caption\": \"Figure 5. Predictive accuracy of learned models trained on individual evidence-type feature groups versus models trained on all features. Each panel shows the results for a learning algorithm applied to all four phenotypes.\", \"page\": 7, \"index\": 4, \"width\": 492, \"height\": 317}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-03-20-712202-v1/fig-005.webp\", \"caption\": \"Figure 6. Predictive accuracy of learned models trained and tested on different phenotypes. Each panel shows the results for one learning method. Test-set phenotypes are grouped along the x-axis. and trainingset phenotypes are indicated by colored bars.\", \"page\": 7, \"index\": 5, \"width\": 492, \"height\": 317}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-03-20-712202-v1/fig-006.webp\", \"caption\": \"Figure 7. ROC curves for random forest models learned on different definitions of negative instances across three phenotypes (panels A to C), and on different target definitions of target nodes for the cholesterol uptake phenotype (panel D).\", \"page\": 7, \"index\": 6, \"width\": 492, \"height\": 404}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-03-20-712202-v1/fig-007.webp\", \"caption\": \"Figure 1. Overview of our graph-based learning approach. We populate a knowledge-graph by extracting information from multiple, public databases. A phenotype of interest P is represented by one or more nodes in the graph (here, u and v). To predict whether a perturbation of gene g will significantly affect P , we consider the relationship of g and P in the knowledge graph. The feature vector x(g,P ) is constructed by concatenating a vector n(g) representing node g, a vector e(g→P ), representing the paths connecting g to one or more nodes in P , and a vector n(P ), representing the node(s) in P to which g is connected by a path (in this example, just node u). A learned model f(·) takes x(g,P ) as input and outputs a binary value as its prediction.\", \"page\": 2, \"index\": 7, \"width\": 484, \"height\": 326}]"
motivation: 基因扰动实验昂贵且费力，需要通过计算模型预测基因扰动对分子表型的影响。
method: 研究采用基于生物网络的图学习模型整合多源证据，预测基因扰动对特定分子表型的影响。
result: 该模型在四种不同表型上表现出较高预测精度，优于多种基准方法，并可在小样本条件下有效学习。
conclusion: 该方法可辅助基因功能探索和实验优先级决策，加速基因-表型关系的研究发现。
---

## 摘要
动机 大规模基因敲低/敲除筛选已被用于深入理解各种表型和生物过程。然而，进行此类实验既昂贵又耗费人力。在本研究中，我们提出了一种基于图的通用机器学习方法，能够在给定部分基因扰动的表型效应的情况下，预测基因扰动对目标分子表型的影响。建立可预测基因扰动效应的模型动机主要有四点：（1）在成本或技术障碍导致无法扰动所有基因的情况下，预测未测量基因的效应；（2）为后续扰动实验优先选择尚未测量的基因或基因集合；（3）推测扰动基因与其效应之间关系的潜在机制；（4）推广至其他尚未测量的目标表型。

结果 我们将所提方法与四种不同的学习算法结合，应用于四种类型的表型建模。实证评估结果显示：(1) 所学习的模型在四种表型上均表现出相对较高的预测精度；(2) 其预测性能优于多个标准基线模型；(3) 即便在较小的训练集上也能学习出准确的模型；(4) 当输入表示中包含多种证据来源时，模型性能进一步提升；(5) 在许多情况下，模型的预测能力可以迁移至其他表型。

数据可用性 本研究所使用的整理数据集及源代码可在以下地址获取：https://github.com/Craven-Biostat-Lab/graph-molecular-phenotype-prediction。

作者总结 获得关于特定生物过程所涉及基因的洞察的一种通用方法，是通过实验扰动单个基因并测量每个扰动对过程的影响。此类大规模实验提供了重要的生物学见解，但通常成本高且操作复杂。因此，往往难以测量对每个基因的扰动效应。本文提出了一种利用现有实验数据和生物网络信息预测基因扰动效应的机器学习方法。该方法可以估计尚未测量的基因的效应，帮助研究人员识别值得下一步研究的候选基因。此外，模型还能提出关于连接基因与目标生物过程的分子相互作用机制的假设。此类方法有助于指导实验研究，加速基因—表型关系的发现。

## Abstract
MotivationLarge-scale gene knockdown/knockout screens have been used to gain insight into a wide array of phenotypes and biological processes. However, conducting such experiments is expensive and labor-intensive. In this work, we present a general graph-based machine-learning approach that can predict the effects of gene perturbations on molecular phenotypes of interest given some measured phenotypic effects of other gene perturbations. The motivation for learning models that can predict the effects of gene perturbations is fourfold. Such models can (1) predict effects for unmeasured genes in cases in which cost or technical barriers preclude perturbing every gene, (2) prioritize unmeasured genes or sets of genes for subsequent perturbation experiments, (3) hypothesize mechanisms that underlie the relationships between the perturbed genes and their effects, and (4) generalize to other unmeasured phenotypes of interest.

ResultsWe evaluate our approach by applying it, in conjunction with four different learning methods, to learn models for four varied phenotypes. Our empirical evaluation demonstrates that the learned models (1) show relatively high levels of predictive accuracy across the four phenotypes, (2) have better predictive accuracy than several standard baselines, (3) can often learn accurate models with small training sets, (4) benefit from having multiple sources of evidence in the input representation, (5) can, in many cases, transfer their predictive value to other phenotypes.

Data availabilityThe assembled data sets and source code for this work are available at: https://github.com/Craven-Biostat-Lab/graph-molecular-phenotype-prediction

Author summaryOne general approach for gaining insight into the genes involved in a specific biological process is to conduct an experiment in which individual genes are perturbed and the effect on the process is measured for each perturbation. Large-scale experiments of this type have provided important biological insights, but they are often expensive and labor-intensive to perform. As a result, it is not always feasible to measure the effects of perturbing every gene. In this article, we present a machine-learning approach to predicting the effects of gene perturbations using available experimental data and biological network information. Our method can estimate the effects of genes that have not yet been experimentally measured, helping researchers identify promising genes to study next. In addition, the models can suggest hypotheses about the molecular interactions that link genes to the biological process of interest. Approaches like this may help guide experimental studies and accelerate the discovery of gene-phenotype relationships.

---

## 论文详细总结（自动生成）

## 一、研究背景与核心问题

- **研究动机**：  
  大规模的基因敲除或敲低实验（如 CRISPR 筛选）是解析基因—表型因果关系的核心手段，但这类实验成本高、执行复杂，不可能覆盖全部基因。  
  因此，迫切需要一种计算方法，基于已有部分扰动实验的数据和生物网络信息，**预测尚未实验扰动的基因对某表型的潜在影响**。  

- **研究目标**：  
  本文提出一种通用的、基于图的机器学习框架，用于预测基因扰动（knockout/knockdown）对多种分子或细胞表型的影响。该模型的目标包括：  
  1. 预测未测基因的表型效应。  
  2. 对后续实验中的基因选择进行优先排序。  
  3. 推断基因作用机制。  
  4. 推广到其他未测表型。

---

## 二、方法论：基于知识图谱的表型预测框架

### 1. 核心思想

- 将基因、表型及其生物关系统一表示为一个**知识图谱（Knowledge Graph, KG）**。  
- 每个节点代表基因或蛋白质；每条边表示功能或物理关联，如蛋白相互作用（PPI）、共表达、通路关系等。  
- 学习一个二分类模型，预测给定基因 \(g\) 是否会显著影响目标表型 \(P\)：  
  \[
  f(x(g, P)) \rightarrow \{0, 1\}
  \]
  其中 1 表示扰动该基因显著影响表型。

### 2. 特征构建

- **输入特征向量** \(x(g,P)\) 由三个部分拼接组成：
  - \(n(g)\)：源基因的特征；
  - \(e(g \rightarrow P)\)：描述基因与表型之间路径关系的特征；
  - \(n(P)\)：表型目标节点的特征。

- **节点特征组（source/target features）**：
  1. **细胞丰度特征**：来自 Human Protein Atlas 的 RNA/蛋白丰度。
  2. **亚细胞定位特征**：基于 UniProt 与 Reactome，构建 41 维二元向量。
  3. **GO 功能特征**：基于 Gene Ontology 构建功能相似度网络，使用 node2vec 嵌入为 64 维向量。

- **关系特征（relation features）**：
  - **证据路径 n-gram**：统计源基因至目标节点路径中 STRING 数据库的证据类型序列（实验E、数据库D、共现T）。
  - **路径置信度得分**：取 STRING “combined score” 的路径乘积。
  - **路径拓扑特征**：最短路径长度、路径数量、节点度等。
  - **随机游走扩散分数**（Random Walk with Restart, RWR）：计算源到表型的扩散相关性。
  - **相似度特征**：源基因与表型节点间 GO 或定位特征的余弦相似度。

### 3. 学习算法

- 框架不依赖特定模型，可结合多种传统监督学习算法训练。本文尝试了以下四个：
  - Elastic Net Logistic Regression  
  - Random Forest  
  - XGBoost  
  - 全连接神经网络（NN，包含一层隐层与 dropout）

- **超参数调优**：在每个训练集内取 10% 数据作为验证集，网格搜索超参数。

---

## 三、实验设计

### 1. 数据集与任务设置

共四种表型（共 4 个数据集）：

| 表型                           | 目标节点（Targets）         | 扰动基因数 | 实例数 | 正样本数 | 细胞类型 |
|--------------------------------|-----------------------------|-------------|---------|-----------|------------|
| 胆固醇稳态 (Cholesterol homeostasis) | SREBP2                     | 18,224      | 18,224  | 191       | HeLa |
| 胆固醇摄取 (Cholesterol uptake) | LDLR                       | 17,768      | 17,768  | 473       | HepG2 |
| 流感病毒复制 (Influenza A replication) | 8个人类宿主蛋白           | 17,856      | 17,856  | 196       | A549 |
| 线粒体蛋白丰度 (Mitochondrial protein abundance) | 57个线粒体蛋白           | 115         | 6,555   | 546       | HAP1 |

#### Label 生成规则：
- 基于原始 CRISPR 筛选实验报告的 MaGeCK 分析结果。  
- 若 FDR < 0.1，则标签为正；否则为负。  
- 对于线粒体数据，q-value < 0.05 视为正。

### 2. 对比基线方法（Benchmarks）

- **最短路径基线**：源基因到目标节点的最短路径长度。  
- **扩散类基线**：三种扩散核方法（RW、RWR、Heat kernel），分别设定不同超参数。  
  - 两种扩散初始化方式：
    - *Target diffusion*：从目标节点扩散；
    - *Positive diffusion*：从目标节点与正样本节点同时扩散。  

### 3. 评估协议

- 所有模型使用 **5 折交叉验证**。
- 采用 **AUROC** 作为主要评估指标。
- 还绘制了 **学习曲线**（随训练样本量变化的性能）。

---

## 四、资源与算力情况

- 文中**未报告**任何关于算力或硬件的信息：
  - 未说明 GPU/CPU 类型、数量或训练时长。
  - 推测由于使用的模型较轻量（传统树模型与小型 MLP），依赖算力较低。
  - 因此未见算力瓶颈。

---

## 五、实验数量与充分性

本文进行的实验维度较多，实验内容充分：

1. **四个表型 × 四种学习算法** → 16 组主实验。  
2. **与六个基线方法**（多核、多参数组合）对比 → 系统基准测试。  
3. **学习曲线分析** → 检验小样本下性能变化。  
4. **特征消融实验**：
   - （1）按图结构部分快分（source、target、relation）。
   - （2）按证据类型分组（丰度、定位、GO、关系）。
5. **跨表型迁移实验**：每个模型在其他三个表型上测试。
6. **鲁棒性实验**：
   - 变更负样本定义（FDR > 0.9）。
   - 改变目标节点集合（单节点 vs 多节点）。
   
结果说明模型稳定性、泛化性和解释性均得验证，实验设计总体**客观且全面**。

---

## 六、主要结论与发现

1. **整体性能优异**：四个表型的平均 AUROC ≈ 0.75，显著优于路径距离和扩散基线。  
2. **对训练样本量不敏感**：少量数据即可学得高性能模型。  
3. **多源证据信息显著增强预测值**：融合定位、表达、GO、PPI 等多类型特征比单类特征更优。  
4. **跨表型迁移能力**：部分模型在未见表型上仍具预测力；除线粒体蛋白丰度外均具可迁移性。  
5. **鲁棒性良好**：负样本定义和目标选择变动不会明显影响性能。

---

## 七、优点与创新

- **方法通用性强**：框架与具体学习模型解耦，适用于广泛的生物表型。  
- **多源知识整合**：整合 STRING、UniProt、Reactome、HPA、GO 等多数据库，形成统一特征表示。  
- **丰富的实验验证**：系统的对比与消融实验，展示了可解释性与稳定性。  
- **可迁移性**：能跨表型预测，拓展未知表型的探索能力。  
- **开源可复现**：提供完整代码与数据链接。

---

## 八、不足与局限

- **预测精度仍有限**：AUROC 约 0.75，说明部分假阳性或假阴性仍存在。  
- **噪声问题**：基因筛选实验自身存在高假阴性率，影响训练数据质量。  
- **表型表示过于简化**：以单个或少数“代理基因节点”表示表型，可能欠拟实际复杂性。  
- **算力与规模未扩展**：未涉及更先进的图神经网络（GNN）或 end-to-end 表征学习；也未报告大规模算力实验。  
- **数据依赖公开数据库**：不同数据库的时效性与覆盖度存在差异，可能引入偏差。  
- **解释性待深化**：缺乏系统的生物机制解释分析。

---

（完）
