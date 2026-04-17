---
title: "TCRseek: Scalable Approximate Nearest Neighbor Search for T-Cell Receptor Repertoires via Windowed k-mer Embeddings"
title_zh: TCRseek：基于窗口化k-mer嵌入的T细胞受体库可扩展近似最近邻搜索
authors: "Yang, Y."
date: 2026-03-24
pdf: "https://www.biorxiv.org/content/10.64898/2026.03.20.713313v1.full.pdf"
tags: ["query:gentcr"]
score: 9.0
evidence: TCR 免疫组库的大规模搜索与嵌入
tldr: 本文提出TCRseek，一种面向T细胞受体序列的可扩展近似最近邻搜索框架。通过窗口化k-mer嵌入和ANN索引结合精确重排名，它显著提升了检索速度并保持高准确率，为大规模TCR序列分析提供了高效的新方案。
source: biorxiv
selection_source: fresh_fetch
figures_json: "[{\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-03-20-713313-v1/fig-001.webp\", \"caption\": \"Table 3: Reranking performance at k = 200.\", \"page\": 25, \"index\": 1, \"width\": 779, \"height\": 278}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-03-20-713313-v1/fig-002.webp\", \"caption\": \"Table 1: ANN-only retrieval performance at best search parameter per index.\", \"page\": 25, \"index\": 2, \"width\": 631, \"height\": 278}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-03-20-713313-v1/fig-003.webp\", \"caption\": \"Table 2: Reranking gains at k = 10 with shortlist k = 1,000. Here R@10 denotes exact-top10 recall, i.e. the fraction of the ground-truth top-10 neighbors recovered in the returned top-10.\", \"page\": 25, \"index\": 3, \"width\": 756, \"height\": 277}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-03-20-713313-v1/fig-004.webp\", \"caption\": \"Table 5: Multi-method retrieval accuracy evaluated against exact ground truth under three distance metrics (10,000 queries, top-10 retrieval from 100,000 sequences). TCRseek uses alignment reranking, while tcrdist3, TCRMatch, and GIANA provide sequence-distance or clustering baselines for comparison.\", \"page\": 26, \"index\": 4, \"width\": 761, \"height\": 373}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-03-20-713313-v1/fig-005.webp\", \"caption\": \"Table 6: Precision@k across methods for alignment and Hamming ground truth at selected k values. GIANA is omitted because its precision remained near zero across all k values.\", \"page\": 26, \"index\": 5, \"width\": 719, \"height\": 214}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-03-20-713313-v1/fig-006.webp\", \"caption\": \"Figure 5: Precision@k curves across methods and ground truth metrics. (A) Alignment, (B) Levenshtein, and (C) Hamming ground truth. TCRseek (blue) remains strongest under alignment and Hamming ground truth, while TCRseek and tcrdist3 are closely matched under Levenshtein ground truth. GIANA is omitted because its precision remained near zero across all k values (see Section 2.10).\", \"page\": 21, \"index\": 6, \"width\": 917, \"height\": 294}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-03-20-713313-v1/fig-007.webp\", \"caption\": \"Figure 6: TCRseek speedup over exact search by index type and distance metric. Speedup increases with the computational cost of the target metric, reaching up to 40× for alignment distance with IVF-PQ.\", \"page\": 22, \"index\": 7, \"width\": 628, \"height\": 375}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-03-20-713313-v1/fig-008.webp\", \"caption\": \"Figure 2: ANN-only retrieval recall@200 across index types and ground truth metrics.\", \"page\": 18, \"index\": 8, \"width\": 535, \"height\": 368}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-03-20-713313-v1/fig-009.webp\", \"caption\": \"Figure 7: Combined results overview. (A) Multi-method NDCG@10 heatmap across three ground truth metrics. (B) Precision@k curves under alignment ground truth. (C) Accuracy-efficiency comparison on the shared stage-A benchmark. (D) TCRseek speedup over exact search by index type and distance metric.\", \"page\": 23, \"index\": 9, \"width\": 915, \"height\": 936}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-03-20-713313-v1/fig-010.webp\", \"caption\": \"Figure 3: Reranking dramatically improves retrieval quality. Paired comparison of ANN-only exact-top10 recall (grey) versus reranked exact-top10 recall (blue) across all index–metric combinations. Exact-top10 recall is the fraction of the ground-truth top-10 neighbors recovered in the returned top-10. Reranking provides +0.31 to +0.63 absolute recall improvement, with the largest gains for IVF-PQ where product quantization introduces the most ranking error.\", \"page\": 19, \"index\": 10, \"width\": 773, \"height\": 378}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-03-20-713313-v1/fig-011.webp\", \"caption\": \"Figure 1: TCRseek two-stage retrieval pipeline. CDR3 amino acid sequences are first encoded into 4,104-dimensional numerical vectors through BLOSUM62 eigendecomposition and multi-scale windowed k-mer embedding (Stage 1), then indexed using FAISS approximate nearest neighbor structures. Retrieved candidates are reranked using exact sequence-level scoring—Needleman–Wunsch alignment, Levenshtein distance, or Hamming distance—to produce a final ranked neighbor list (Stage 2).\", \"page\": 17, \"index\": 11, \"width\": 854, \"height\": 181}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-03-20-713313-v1/fig-012.webp\", \"caption\": \"Figure 8: Sensitivity of retrieval accuracy to shortlist size. Top row: binary top-200 recall@10, defined as the number of ground-truth top-200 neighbors recovered in the returned top-10 divided by 200; its theoretical maximum is 0.05. Bottom row: exact-top10 recall, defined as the fraction of true top-10 neighbors recovered in the reranked output. Columns correspond to Hamming, Levenshtein, and alignment ground truth metrics. Binary top-200 recall@10 approaches its 0.05 ceiling rapidly, whereas exact-top10 recall continues to improve with larger shortlists and more clearly separates index types.\", \"page\": 24, \"index\": 12, \"width\": 931, \"height\": 466}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-03-20-713313-v1/fig-013.webp\", \"caption\": \"Figure 4: Multi-method retrieval accuracy heatmap. NDCG@10 for TCRseek, tcrdist3, TCRMatch, and GIANA (rows) evaluated against three ground truth distance metrics (columns). TCRseek is strongest under alignment and Hamming ground truth, while TCRseek and tcrdist3 are nearly tied under Levenshtein ground truth.\", \"page\": 20, \"index\": 13, \"width\": 536, \"height\": 506}]"
motivation: TCR测序数据快速增长，现有方法在大规模检索中面临计算量大或灵敏度低的限制。
method: 该方法结合k-mer窗口嵌入与近似最近邻索引，并通过精确比对模块进行结果重排名。
result: TCRseek在保证准确性的同时实现了3.6至39.6倍的搜索加速，并在多种距离度量下表现优异。
conclusion: TCRseek在准确率和计算效率上均具优势，为TCR受体库高效比对提供了可扩展的解决方案。
---

## 摘要
T细胞受体（T-cell receptor, TCR）测序数据的迅速增长，迫切需要能够在大规模条件下高效搜索CDR3序列的计算方法。现有方法要么依赖于精确的成对距离计算，其计算量随库规模平方增长；要么采用牺牲敏感度的启发式分组策略。本文提出了TCRseek，这是一种两阶段的检索框架，结合了具有生物学意义的序列嵌入与近似最近邻（Approximate Nearest Neighbor, ANN）索引，从而实现对TCR库的可扩展检索。TCRseek首先通过基于BLOSUM62特征分解的多尺度窗口化k-mer嵌入方案，将CDR3氨基酸序列编码为固定长度的数值向量；然后利用FAISS结构（IVF-Flat、IVF-PQ或HNSW-Flat）对这些向量建立索引，实现亚线性时间的搜索。第二阶段的重排序模块利用精确的序列比对得分（Needleman-Wunsch算法配合BLOSUM62矩阵）、Levenshtein距离或Hamming距离，对初筛候选进行优化。我们在一个包含100,000条序列并预计算三种距离度量下精确真值的语料库中，将TCRseek与tcrdist3、TCRMatch和GIANA进行了基准测试。在跨度量评估中——即重排序度量与真值度量不同，这种评估最能反映算法泛化能力——TCRseek在Levenshtein真值下取得NDCG@10 = 0.890，在Hamming真值下取得0.880，在Hamming条件下排名最高，并在Levenshtein条件下保持与tcrdist3（0.894）相当的性能。当重排序度量与真值定义（BLOSUM62比对）一致时，NDCG@10达到0.993，表明ANN初筛捕获了超过99%的真实邻居，验证了两阶段设计的理论上限。在该10万序列语料库上，TCRseek相对于精确的穷举搜索实现了3.6–39.6倍的速度提升，具体取决于索引类型和距离度量，其中以基于比对的检索提升最大。这些结果表明，基于嵌入的ANN搜索为TCR库分析提供了一种实用且可扩展的替代方案。

## Abstract
The rapid growth of T-cell receptor (TCR) sequencing data has created an urgent need for computational methods that can efficiently search CDR3 sequences at scale. Existing approaches either rely on exact pairwise distance computation, which scales quadratically with repertoire size, or employ heuristic grouping that sacrifices sensitivity. Here we present TCRseek, a two-stage retrieval framework that combines biologically informed sequence embeddings with approximate nearest neighbor (ANN) indexing for scalable search over TCR repertoires. TCRseek first encodes CDR3 amino acid sequences into fixed-length numerical vectors through a multi-scale windowed k-mer embedding scheme derived from BLOSUM62 eigendecomposition, then indexes these vectors using FAISS-based structures (IVF-Flat, IVF-PQ, or HNSW-Flat) that support sublinear-time search. A second-stage reranking module refines the shortlisted candidates using exact sequence alignment scores (Needleman-Wunsch with BLOSUM62), Levenshtein distance, or Hamming distance. We benchmarked TCRseek against tcrdist3, TCRMatch, and GIANA on a 100,000-sequence corpus with precomputed exact ground truth under three distance metrics. Under cross-metric evaluation--where the reranking and ground truth metrics differ, providing the most informative test of generalization--TCRseek achieved NDCG@10 = 0.890 (Levenshtein ground truth) and 0.880 (Hamming ground truth), ranking highest among the retained baselines under Hamming and remaining competitive with tcrdist3 (0.894) under Levenshtein. When the reranking metric matches the ground truth definition (BLOSUM62 alignment), NDCG@10 reached 0.993, confirming that the ANN shortlist captures >99% of true neighbors--the expected ceiling of the two-stage design. On the 100,000-sequence corpus, TCRseek achieved 3.6-39.6x speedup over exact brute-force search depending on index type and distance metric, with the largest gains for alignment-based retrieval. These results demonstrate that embedding-based ANN search provides a practical and scalable alternative for TCR repertoire analysis.

---

## 论文详细总结（自动生成）

# TCRseek：基于窗口化 k-mer 嵌入的 T 细胞受体库可扩展近似搜索  
——论文结构化分析总结

---

## 一、研究问题与背景

- **研究动机**  
  随着高通量测序技术的发展，T 细胞受体（T-cell receptor, TCR）测序库规模迅速扩大，常见样本规模可以达到数百万条 CDR3 序列。传统的序列比对或距离计算（如 Needleman–Wunsch 或 Levenshtein）需进行成对比较，计算复杂度为 \(O(n^2)\)，难以适应大规模数据库检索。  

- **核心问题**  
  论文关注如何在保证生物学相关性的前提下，大幅提升 TCR 相似性搜索的计算效率，使其能在百万级序列规模下实现亚线性时间的检索。

- **研究意义**  
  通过提出一种可扩展、嵌入驱动的近似最近邻（Approximate Nearest Neighbor, ANN）框架，论文为免疫组学数据的快速比对、克隆相似性分析及免疫多样性研究提供了新的计算工具。

---

## 二、方法论：TCRseek 框架设计

### 1. 核心思想
- 将 **氨基酸序列空间映射至连续的嵌入空间**，以便利用高维索引结构实现近似检索；
- 采用 **两阶段搜索策略**：
  1. **阶段一：ANN 初筛** —— 通过窗口化 k-mer 嵌入向量实现快速近似搜索；
  2. **阶段二：精确重排序** —— 对初筛候选集进行精确的序列级比对或距离计算。

### 2. 关键技术细节

- **编码机制**  
  - 使用 BLOSUM62 矩阵的特征分解（eigendecomposition）捕捉氨基酸之间的替换关系；  
  - 采用多尺度窗口化（windowed）k-mer 方案，提取不同 k 值的局部序列模式；
  - 将每条 CDR3 序列编码为 **4,104 维固定长度向量**。

- **索引结构（Stage 1）**  
  基于 **FAISS** 库构建 ANN 索引，包含三种实现选项：
  - **IVF-Flat**：基于倒排文件的精确量化索引；
  - **IVF-PQ**：采用产品量化（product quantization），在牺牲部分精度的情况下提供最高速度；
  - **HNSW-Flat**：图结构索引，兼顾准确率与搜索速度。

- **候选重排序（Stage 2）**
  - 使用 Needleman–Wunsch 算法结合 BLOSUM62 评分矩阵；
  - 或采用 **Levenshtein** 距离与 **Hamming** 距离；
  - 以精确得分对候选集重新排名，构造最终结果。

- **性能指标**
  - 准确性：使用 NDCG@10、Recall@k、Precision@k；
  - 规模效应：速度提升倍数（speedup）相对于完全穷举比对。

---

## 三、实验设计

- **数据集**  
  - 构建包含 **100,000 条 TCR CDR3 序列**的语料；
  - 对每一对序列预计算三种真值距离（Alignment、Levenshtein、Hamming），确保可获得“精确真值”（ground truth）。

- **对比方法（Benchmark Baselines）**  
  - **tcrdist3**：广泛使用的基于子区域距离的TCR相似性测度；
  - **TCRMatch**：基于一致性比对的启发式检索；
  - **GIANA**：基于聚类的 TCR 相似性搜索工具。

- **评估方式**
  - 同指标评估：重排序度量与真值相同；
  - **跨指标评估（cross-metric）**：重排序度量与真值不同，用于检测模型的泛化能力；
  - 性能度量集中于 NDCG@10、Precision@k、Recall@k。

---

## 四、计算资源与算力

- 论文未明确描述所用硬件配置、GPU 类型或运行时长；
- 仅报告了速度比值（speedup），说明为软件层面效率测试，而非模型训练；
- 可推测评估在普通 CPU / GPU 混合环境下进行，但未给出具体算力规模。

---

## 五、实验数量与充分性

- **数量层面**  
  实验在三个距离指标 × 三种索引结构 × 三种重排序方式 × 四个对比方法的全组合上展开；
  同时进行了不同 shortlist 大小与不同精度/速度权衡设置的评估。

- **充分性与公平性**  
  - 每项性能分析都在同一语料和相同真值定义下进行；
  - 包含对 ANN-only 与 reranked 的分层对比；
  - 提供跨指标与同指标两个维度的结果；
  → 可认为实验设计较为系统、全面。

---

## 六、主要结论与发现

- **准确性**
  - 在 same-metric（比对真值）条件下，TCRseek 达到 **NDCG@10 = 0.993**；
  - 在 cross-metric 评估中，Levenshtein 真值下 0.890，Hamming 真值下 0.880；
  - 在大多数指标和真值下均优于或匹敌 tcrdist3。

- **效率**
  - 相对于穷举法，实现 **3.6–39.6 倍**加速；
  - 最大速度提升出现在 alignment 计算情景下。

- **泛化性**
  - 结果在三种 ground truth 之间保持较稳定；
  - ANN 初筛阶段能捕获超过 99% 的真实邻居。

---

## 七、优点与亮点

- **算法创新**
  - 将多尺度窗口化 k-mer 嵌入与 ANN 索引结合，是 TCR 序列检索领域较新的方向；
  - 设计了两阶段（embedding + alignment reranking）架构，有良好的理论上限。

- **性能表现**
  - 同时提升准确性与计算效率；
  - 系统评估不同索引、距离和 shortlist 尺度下的性能。

- **可扩展性**
  - 基于 FAISS，可在百万级数据规模上线性扩展；
  - 嵌入维度固定，使新增数据的索引成本较低。

---

## 八、不足与局限

- **资源信息缺失**：论文未披露硬件条件、内存占用及并行优化策略；
- **数据集覆盖有限**：仅使用单一 TCR 库，缺乏跨物种、不同实验条件的数据验证；
- **生物学解释性有限**：嵌入向量与免疫表位或功能关系的可解释性未深入讨论；
- **对超大规模（>10⁶ 序列）验证不足**：当前最多评估 10 万条序列；
- **方法依赖于 BLOSUM62**：未探讨其他替代表征矩阵或任务特化嵌入的适应性。

---

**（完）**
