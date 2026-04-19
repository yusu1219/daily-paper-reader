---
title: "Hybrid Gated Fusion: A Multimodal Deep Learning Framework for Protein Function Annotation"
title_zh: 混合门控融合：一种用于蛋白质功能注释的多模态深度学习框架
authors: "Zhou, Z., Buchan, D. W."
date: 2026-04-17
pdf: "https://www.biorxiv.org/content/10.64898/2026.04.14.718564v1.full.pdf"
tags: ["query:gentcr"]
score: 6.0
evidence: 整合序列和结构的蛋白质功能注释多模态深度学习
tldr: 本文提出Hybrid Gated Fusion框架以解决蛋白功能注释中的多模态融合难题，通过双线性门控强化模态信息评估与一致性学习，并辅以辅助监督减少模态主导，最终在CAFA3基准上取得突破性性能。
source: biorxiv
selection_source: fresh_fetch
figures_json: "[{\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-04-14-718564-v1/fig-001.webp\", \"caption\": \"Table 2 Comparative performance on CAFA3 in terms of Fmax. Seq, Text, Struct, PPI, and Hom denote sequence, text, structure, PPI, and homology inputs, respectively. Results for sequence-based and homologybased methods are from Oliveira et al. (2023), while those for TransFun, DeepGraphGO, and the DualNetGO variants are from Chen and Luo (2024). Ours denotes a single trained model with dynamic masking. Best values are shown in bold; second-best values are underlined.\", \"page\": 7, \"index\": 1, \"width\": 490, \"height\": 513}]"
motivation: 现有多模态蛋白功能注释方法在处理输入缺失和信息冗余时表现不佳，亟需更稳健的融合框架。
method: 提出名为Hybrid Gated Fusion的多模态深度学习架构，通过双线性门控机制融合蛋白序列、结构、文本及网络等多源信息。
result: 该模型在CAFA3基准上的生物过程、细胞组分和分子功能任务均取得领先的F_max表现。
conclusion: Hybrid Gated Fusion证明了多模态门控融合在增强蛋白功能注释鲁棒性和可扩展性方面的有效性。
---

## 摘要
蛋白质功能注释需要整合多种生物学信号，但现有的多模态方法往往难以应对输入缺失和冗余信息的问题。我们提出了混合门控融合（Hybrid Gated Fusion），这是一种多模态架构，将蛋白质的内在特征（包括序列和结构）与来自文本和相互作用网络的外在功能背景相结合。与对所有模态赋予相同权重的方法不同，该模型使用双线性门控机制来评估每个模态的信息量及其与其他模态的一致性，同时通过辅助监督减少模态支配效应，并在较弱模态中保留有用信号。在 CAFA3 基准测试中，单个 Hybrid Gated Fusion 模型在生物过程（F_max = 0.601）和细胞组分（F_max = 0.706）上达到了当前最优性能，并在分子功能（F_max = 0.702）上保持竞争力。对学习到的门控机制的分析表明，相互作用网络和文本通常提供互补的功能信号，而结构特征在信息冗余时被降低权重，但在输入稀疏的情况下仍然具有价值。这些结果表明，Hybrid Gated Fusion 是一种稳健且可扩展的基因组尺度蛋白质功能注释框架。

## Abstract
Protein function annotation requires integrating diverse biological signals, yet existing multimodal methods often struggle with missing inputs and redundant information. We present Hybrid Gated Fusion, a multimodal architecture that combines intrinsic protein features, including sequence and structure, with extrinsic functional context from text and interaction networks. Rather than weighting all modalities equally, the model uses bilinear gating to assess both the informativeness of each modality and its agreement with the others, while auxiliary supervision reduces modality dominance and preserves useful signal in weaker modalities. On the CAFA3 benchmark, a single Hybrid Gated Fusion model achieves state-of-the-art performance in Biological Process (F_max = 0.601) and Cellular Component (F_max = 0.706), while remaining competitive in Molecular Function (F_max = 0.702). Analysis of the learned gates shows that interaction networks and text often provide complementary functional signals, whereas structural features are down-weighted when redundant but remain valuable under sparse-input settings. These results establish Hybrid Gated Fusion as a robust and scalable framework for genome-scale protein function annotation.