---
title: A graph-based learning approach to predict the effects of gene perturbations on molecular phenotypes
title_zh: 一种基于图的学习方法，用于预测基因扰动对分子表型的影响
authors: "Jin, Y., Sverchkov, Y., Sushkova, A., Ohtake, M., Emfinger, C., Craven, M."
date: 2026-03-25
pdf: "https://www.biorxiv.org/content/10.64898/2026.03.20.712202v2.full.pdf"
tags: ["query:virtcell"]
score: 9.0
evidence: 使用基于图的机器学习预测基因扰动对分子表型的影响
tldr: 该研究旨在以图为基础的机器学习方法预测基因扰动对分子表型的影响，解决实验成本高的问题。研究利用生物网络和已知表型数据训练模型，实现对未测基因的有效预测，并在多个表型上显著超过传统基线方法，为基因功能研究提供高效工具。
source: biorxiv
selection_source: fresh_fetch
figures_json: "[{\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-03-20-712202-v2/fig-001.webp\", \"caption\": \"Fig 3. Learning curves for baseline methods and the learning methods. Each panel shows the results for one phenotype. The x-axis shows the fraction of the available training set used and y-axis shows the resulting AUROC values.\", \"page\": 11, \"index\": 1, \"width\": 792, \"height\": 711}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-03-20-712202-v2/fig-002.webp\", \"caption\": \"Fig 7. ROC curves for random forest models learned on different definitions of negative instances across three phenotypes (panels A to C), and on different target definitions of target nodes for the cholesterol uptake phenotype (panel D).\", \"page\": 15, \"index\": 2, \"width\": 792, \"height\": 618}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-03-20-712202-v2/fig-003.webp\", \"caption\": \"Table 1. Detailed description of data sets for each phenotype.\", \"page\": 7, \"index\": 3, \"width\": 1196, \"height\": 221}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-03-20-712202-v2/fig-004.webp\", \"caption\": \"Fig 6. Predictive accuracy of learned models trained and tested on different phenotypes. Each panel shows the results for one learning method. Test-set phenotypes are grouped along the x-axis, training-set phenotypes are indicated by colored bars, and the feature sets used are distinguished by bar fill styles: solid for all features and hatched for ST-relation features\", \"page\": 14, \"index\": 4, \"width\": 793, \"height\": 493}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-03-20-712202-v2/fig-005.webp\", \"caption\": \"Fig 1. Overview of our graph-based learning approach. We populate a knowledge-graph by extracting information from multiple, public databases. A phenotype of interest P is represented by one or more nodes in the graph (here, u and v). To predict whether a perturbation of gene g will significantly affect P , we consider the relationship of g and P in the knowledge graph. The feature vector x(g,P ) is constructed by concatenating a vector n(g) representing node g, a vector e(g→P ), representing the paths connecting g to one or more nodes in P , and a vector n(P ), representing the node(s) in P to which g is connected by a path (in this example, just node u). A learned model f(·) takes x(g,P ) as input and outputs a binary value as its prediction.\", \"page\": 3, \"index\": 5, \"width\": 778, \"height\": 526}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-03-20-712202-v2/fig-006.webp\", \"caption\": \"Fig 5. Predictive accuracy of learned models trained on individual evidence-type feature groups versus models trained on all features. Each panel shows the results for a learning algorithm applied to all four phenotypes.\", \"page\": 13, \"index\": 6, \"width\": 793, \"height\": 493}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-03-20-712202-v2/fig-007.webp\", \"caption\": \"Fig 4. Predictive accuracy of learned models trained on individual subgraph feature groups versus models trained on all features. Each panel shows the results for a learning algorithm applied to all four phenotypes.\", \"page\": 12, \"index\": 7, \"width\": 793, \"height\": 492}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-03-20-712202-v2/fig-008.webp\", \"caption\": \"Fig 2. Predictive accuracy of the four learning algorithms for the four phentoypes. Each panel shows the ROC curves and AUROC values for each learning method on the given phenotype.\", \"page\": 9, \"index\": 8, \"width\": 793, \"height\": 710}]"
motivation: 由于大规模基因敲除实验成本高昂且操作繁琐，亟需通过计算方法预测未测基因的表型效应。
method: 提出了一种利用基因网络信息和已测表型数据的图学习模型来预测未测基因的扰动效应。
result: 模型在四种不同表型上表现出高预测精度，优于多种基线方法，并能在小样本下保持良好性能。
conclusion: 该研究表明基于图的机器学习方法能有效预测基因扰动对分子表型的影响，为后续实验设计提供指导。
---

## 摘要
研究动机 大规模的基因敲低/敲除筛选已被用于深入理解各种表型和生物学过程。然而，开展此类实验成本高昂且劳动密集。在本研究中，我们提出了一种通用的基于图的机器学习方法，可以在已知部分基因扰动的表型效应的前提下，预测其他基因扰动对目标分子表型的影响。开发能够预测基因扰动效应的模型具有四个动机：(1) 在成本或技术障碍使得难以扰动所有基因的情况下，预测未测量基因的效应；(2) 为后续扰动实验优先选择未测量的基因或基因集；(3) 提出解释扰动基因与其效应之间关系的潜在机制假设；(4) 推广至其他尚未测量的目标表型。

研究结果 我们结合四种不同的学习方法，将所提出的模型应用于四种异质表型的学习任务进行评估。实证结果表明，所学习的模型 (1) 在四种表型上表现出较高的预测准确性；(2) 在预测精度上优于若干标准基线模型；(3) 即使在较小训练集下也能学习到准确的模型；(4) 在输入表示中结合多种证据信息时性能更优；(5) 在许多情况下，其预测能力可迁移到其他表型。

数据可用性 本研究的数据集与源代码可通过以下链接获取：https://github.com/Craven-Biostat-Lab/graph-molecular-phenotype-prediction

作者总结 理解特定生物过程所涉及基因的一般方法是进行实验，使单个基因发生扰动并测量其对过程的影响。此类大规模实验为生物学研究提供了重要的见解，但通常成本高且过程繁琐，因此无法总是对所有基因的扰动效应进行测量。本文提出了一种基于实验数据与生物网络信息的机器学习方法，用于预测基因扰动的效应。该方法能估计尚未被实验测量的基因效应，帮助研究者识别值得优先研究的候选基因。此外，该模型还能提出关于基因与目标生物过程之间分子相互作用的假设。此类方法有助于指导实验研究并加速基因-表型关系的发现。

## Abstract
MotivationLarge-scale gene knockdown/knockout screens have been used to gain insight into a wide array of phenotypes and biological processes. However, conducting such experiments is expensive and labor-intensive. In this work, we present a general graph-based machine-learning approach that can predict the effects of gene perturbations on molecular phenotypes of interest given some measured phenotypic effects of other gene perturbations. The motivation for learning models that can predict the effects of gene perturbations is fourfold. Such models can (1) predict effects for unmeasured genes in cases in which cost or technical barriers preclude perturbing every gene, (2) prioritize unmeasured genes or sets of genes for subsequent perturbation experiments, (3) hypothesize mechanisms that underlie the relationships between the perturbed genes and their effects, and (4) generalize to other unmeasured phenotypes of interest.

ResultsWe evaluate our approach by applying it, in conjunction with four different learning methods, to learn models for four varied phenotypes. Our empirical evaluation demonstrates that the learned models (1) show relatively high levels of predictive accuracy across the four phenotypes, (2) have better predictive accuracy than several standard baselines, (3) can often learn accurate models with small training sets, (4) benefit from having multiple sources of evidence in the input representation, (5) can, in many cases, transfer their predictive value to other phenotypes.

Data availabilityThe assembled data sets and source code for this work are available at: https://github.com/Craven-Biostat-Lab/graph-molecular-phenotype-prediction

Author summaryOne general approach for gaining insight into the genes involved in a specific biological process is to conduct an experiment in which individual genes are perturbed and the effect on the process is measured for each perturbation. Large-scale experiments of this type have provided important biological insights, but they are often expensive and labor-intensive to perform. As a result, it is not always feasible to measure the effects of perturbing every gene. In this article, we present a machine-learning approach to predicting the effects of gene perturbations using available experimental data and biological network information. Our method can estimate the effects of genes that have not yet been experimentally measured, helping researchers identify promising genes to study next. In addition, the models can suggest hypotheses about the molecular interactions that link genes to the biological process of interest. Approaches like this may help guide experimental studies and accelerate the discovery of gene-phenotype relationships.

---

## 论文详细总结（自动生成）

# 一种基于图的学习方法，用于预测基因扰动对分子表型的影响  
**论文来源：** bioRxiv，2026年3月25日  
**作者：** Yiyang Jin 等  
**机构：** 威斯康星大学、斯坦福大学等  
**研究主题：** 利用知识图（biological knowledge graph）和机器学习预测基因扰动对分子表型的影响  

---

## 一、研究核心问题与背景

- **核心问题：**  
  基因敲除/敲低实验是理解基因功能与表型关系的重要手段，但大规模实验成本高昂、效率低下。研究者希望通过计算模型预测未实验扰动的基因对分子表型的潜在影响。

- **研究动机：**  
  传统基于实验的表型推断无法全面覆盖所有基因；已有深度学习模型通常仅能预测单一表型（如基因致死性），缺乏跨表型的泛化能力。  
  因此，本研究设计一种**面向多表型、可泛化的图学习框架**，整合多源生物信息（PPI 网络、GO 注释、蛋白定位等），实现对未测基因扰动的预测。

---

## 二、方法论：图学习的核心思想与关键技术

### 1. 核心思想
- 将**基因、表型及它们的关联关系表示为知识图（Knowledge Graph）**。  
- 每个基因（source node）和表型（target node）均为图中的节点，它们通过多层关系边连接。  
- 构建特征向量 \(x(g, P)\)，表示基因 *g* 对表型 *P* 的潜在效应，再用机器学习模型预测扰动是否显著影响表型。

### 2. 特征构成
特征向量由三部分组成：
1. **源节点特征 \(n(g)\)**：描述基因本身属性。  
2. **目标节点特征 \(n(P)\)**：描述表型对应目标节点的属性。  
3. **源-目标关系特征 \(e(g→P)\)**：编码基因与表型之间在图中的路径结构和连通性特征。

### 3. 图构建与特征计算
- 使用多个公共数据库：
  - STRING（蛋白互作网络与证据等级）  
  - UniProt、Reactome（亚细胞定位与通路信息）  
  - Human Protein Atlas（蛋白表达丰度）  
  - Gene Ontology（功能注释）  
- GO 注释利用 **Jaccard 相似度 + node2vec 嵌入** 生成 64 维特征。
- 关系特征包括：
  - 路径的证据类型 *n-gram* 编码（实验、数据库或文献证据）。  
  - 交互置信度分数乘积。  
  - 拓扑特征（最短路径长度、节点度分布、路径数量）。  
  - **随机游走与重启（Random Walk with Restart, RWR）**扩散得分，模拟基因到表型的影响传播。  
  - 源与目标特征的相似度（如余弦相似度）。

### 4. 学习模型
使用四种经典的机器学习算法进行训练：
- Elastic Net Logistic Regression  
- Random Forest  
- XGBoost  
- Neural Networks（1-2 层全连接网络，ReLU/Sigmoid 激活）

每种算法均通过**五折交叉验证**调节超参数。

---

## 三、实验设计

### 1. 数据集来源与表型场景
研究共使用四种表型，数据来自多个大规模 CRISPR 基因筛选实验：

| 表型 | 目标节点 | 扰动基因数 | 实例总数 | 阳性样本 | 细胞类型 |
|------|-----------|-------------|-----------|-----------|-----------|
| 胆固醇稳态 | SREBP2 | 18,224 | 18,224 | 191 | HeLa |
| 胆固醇摄取 | LDLR | 17,768 | 17,768 | 473 | HepG2 |
| 流感病毒复制 | 8 个宿主蛋白 | 17,856 | 17,856 | 196 | A549 |
| 线粒体蛋白丰度 | 57 个线粒体蛋白 | 115 | 6,555 | 546 | HAP1 |

标注规则：
- MaGeCK 分析中 FDR < 0.1 为正例。
- 线粒体数据集中 q-value < 0.05 为正例。

### 2. Benchmark 与对比方法
与两类基线方法比较：
1. **最短路径长度（Shortest Path Length）**
2. **扩散核（Diffusion-based Methods）**
   - Random Walk (RW)
   - Random Walk with Restart (RWR)
   - Heat Kernel  
   这些方法在“目标扩散”和“正例扩散”两种模式下运行。

### 3. 模型评估
- 采用 AUROC（ROC 曲线下面积）评估分类性能。
- 做学习曲线与特征消融分析。
- 还进行了**跨表型迁移学习实验**和**数据敏感性分析**。

---

## 四、资源与算力

- **论文中未说明具体算力配置**（如 GPU 型号、数量、训练时长或硬件环境）。  
- 因模型规模较小（浅层神经网络与树模型），推测可在中等计算资源上完成（例如单 GPU 或 CPU 集群）。  
- 该点是论文在技术复现性方面的不足。

---

## 五、实验数量与充分性

- **实验组别：**
  1. 四个表型 × 四种学习算法（基本性能评估）  
  2. 与六类基线方法比较（包括不同扩散核与参数）  
  3. 不同训练集比例的学习曲线分析  
  4. 特征消融实验：分别测试三大子特征组与四种证据类型特征  
  5. 跨表型迁移实验（训练于一种表型，测试于另一表型）  
  6. 数据集敏感性分析（改变负样本定义与目标节点选择）

- **实验覆盖度与充分性：**
  - 实验数量多、覆盖全面；包括对模型泛化、跨域性、特征效应的系统检验。  
  - 数据来源均为公开 CRISPR 库，评价指标统一，保证了**客观与公平性**。  
  - 无明显过拟合或数据泄漏迹象。

---

## 六、主要结论与发现

1. 所提出的图学习模型在四种表型上平均 AUROC ≈ 0.72，表现稳定且高于所有基线。  
2. 模型在小训练集条件下仍可获得较高精度，显示出强的样本效率。  
3. 不同信息源（PPI、GO、定位、丰度）共同提升模型性能；多证据融合最优。  
4. **关系特征（source–target relation features）**对性能贡献最大，可在跨表型任务中保持预测能力。  
5. 模型可在一种表型训练后迁移至另一表型，具备跨任务泛化能力。  
6. 模型对“负样本定义”和“目标节点选取”的敏感性较低，说明方法稳健。

---

## 七、优点与创新点

- **多源信息整合：** 同时利用蛋白互作、GO 功能、定位和表达量等不同数据，构建丰富的节点与路径特征。  
- **模型通用性强：** 适用于任何表型，只需在知识图中定义相应目标节点。  
- **跨表型迁移能力：** 可将学习到的关系规律应用于未训练的表型。  
- **实验设计全面：** 涵盖模型性能、消融、迁移、敏感性等多角度验证。  
- **开源数据与代码：** 提供了完整的可复现资源。

---

## 八、不足与局限

- **预测准确率仍有提升空间**：平均 AUROC≈0.72，说明模型仍受数据噪声与标签不平衡影响。  
- **算力与训练细节未公开**：影响方法复现与公平比较。  
- **依赖现有知识图质量**：STRING 与 GO 的缺失或偏差会影响特征表示。  
- **对复杂表型的定义限制**：当前假设表型可用少数“代理节点”表示，不适用于过程性或系统性表型。  
- **无法解释性不足**：虽具预测力，但尚需解释基因–表型关系的机制。  
- **未与深度图神经网络（如 GNN）直接比较**：限制了方法在现代深度学习框架中的定位。

---

（完）
