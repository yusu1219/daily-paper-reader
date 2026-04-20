---
title: "found: Inferring cell-level perturbation from structured label noise in single-cell data"
title_zh: found：从单细胞数据中的结构化标签噪声推断细胞级扰动
authors: "Afanasiev, E., Goeva, A."
date: 2026-04-14
pdf: "https://www.biorxiv.org/content/10.64898/2026.04.10.717768v1.full.pdf"
tags: ["query:virtcell"]
score: 7.5
evidence: 从结构化标签噪声中推断细胞级扰动
tldr: 本研究开发了found工具，是HiDDEN方法的Python和R实现，用于在无需已知受影响群体的情况下从批次级标签中推断细胞水平扰动。该框架支持灵活的管线配置、超参数调节和可视化，并在多数据集基准测试中展现了依赖于建模选择的稳健性能，为单细胞扰动分析提供了高效实用的解决方案。
source: biorxiv
selection_source: fresh_fetch
figures_json: "[{\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-04-10-717768-v1/fig-001.webp\", \"caption\": \"Figure 1: HiDDEN/found overview and demonstration A: Schematic of the HiDDEN pipeline, including embedding, continuous scoring, and discretization steps. B: Example usage of the found library in Python. C: Example usage of the found library in R. D: Example usage of visualization utilities from the found.pl module in Python. E: Evaluation of HiDDEN outputs on IL-15-stimulated PBMC data (PBS as control).\", \"page\": 17, \"index\": 1, \"width\": 918, \"height\": 380}]"
motivation: 传统的样本级标签常无法捕捉异质的细胞水平扰动效应，需要更精细的分析方法。
method: 该研究提出了found，一个在Python和R中实现的用于单细胞数据扰动推断的HiDDEN框架。
result: found在多个数据集中表现稳定，其性能与回归模型、分组策略及嵌入维度的选择密切相关。
conclusion: found为单细胞扰动效应分析提供了一个灵活且易用的计算框架，提升了结果的鲁棒性与可解释性。
---

## 摘要
Goeva 等人近期提出的 HiDDEN 方法，旨在通过优化批次级标签，在无需事先了解受影响群体的情况下推断单细胞水平的扰动，从而解决样本级标签与细胞间异质扰动效应之间的不匹配问题。

在本研究中，我们提出了 found，这是一种在 Python 和 R 中实现的 HiDDEN 工具，支持流程定制、按因子分组、超参数选择和可视化。通过在多样化数据集上的基准测试，我们发现性能强烈依赖于建模选择，特别是回归方法、分组策略和嵌入维度。found 提供了一个实用、灵活且易于使用的框架，用于稳健的单细胞扰动分析。

## Abstract
Recent work by Goeva et al. introduced HiDDEN, a method for refining batch-level labels to infer cell-level perturbation without prior knowledge of affected populations, addressing the mismatch between sample-level labels and heterogeneous perturbation effects across cells.

Here, we present found, a Python and R implementation of HiDDEN, supporting pipeline customization, by-factor grouping, hyperparameter selection, and visualization. Through benchmarking across diverse datasets, we show that performance depends strongly on modeling choices, particularly regression, grouping, and embedding dimensionality. found provides a practical, flexible, and accessible framework for robust cell-level perturbation analysis.