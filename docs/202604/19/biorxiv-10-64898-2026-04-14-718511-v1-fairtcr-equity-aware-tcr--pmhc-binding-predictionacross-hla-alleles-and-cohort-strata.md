---
title: "FairTCR: Equity-Aware TCR--pMHC Binding Prediction\\\\Across HLA Alleles and Cohort Strata"
title_zh: FairTCR：面向公平性的跨 HLA 等位基因与队列分层的 TCR–pMHC 结合预测
authors: "Nowak, P., Kowalski, J., Lewandowski, T."
date: 2026-04-17
pdf: "https://www.biorxiv.org/content/10.64898/2026.04.14.718511v1.full.pdf"
tags: ["query:gentcr"]
score: 7.0
evidence: 跨HLA等位基因的TCR-pMHC结合预测与优化
tldr: 本文提出FairTCR框架，通过分组分布鲁棒优化(GDRO)减轻TCR–pMHC结合预测中HLA等位基因和人群不平衡导致的性能差异，实现更公平的预测性能，显著提升稀有等位基因组的AUPRC表现。
source: biorxiv
selection_source: fresh_fetch
figures_json: "[{\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-04-14-718511-v1/fig-001.webp\", \"caption\": \"TABLE II DATASET AND SPLIT SUMMARY (ALL HLA SUPERTYPES COMBINED).\", \"page\": 3, \"index\": 1, \"width\": 529, \"height\": 352}]"
motivation: 现有TCR–pMHC结合预测数据集中HLA等位基因和人群分布极度不平衡，导致模型在稀有等位基因和代表性不足群体上表现不佳。
method: 采用基于在线指数梯度更新的GDRO方法，最小化HLA超型和群体分层的最差组损失。
result: "FairTCR在VDJdb–IEDB基准上将平均与最差组AUPRC差距从0.190降至0.098，减少48.4%的不公平性，同时保持整体性能。"
conclusion: FairTCR有效提升TCR–pMHC预测在不同HLA等位基因和不同人群间的公平性，实现性能与公平性的平衡。
---

## 摘要
公共的 TCR–pMHC 结合数据库在分布上严重偏向于少数几个研究较多的 HLA 等位基因——最显著的是 HLA-A*02:01，其占已整理记录的约 45%——以及来自欧洲血缘队列的患者。基于此类数据训练的标准经验风险最小化（ERM）模型在总体精度上表现良好，但常常在罕见等位基因和代表性不足的队列上表现不佳，从而造成在单一指标基准测试中不可见的系统性差异。我们提出了 FairTCR，这是一种群体分布鲁棒优化（GDRO）框架，通过在线指数梯度更新最小化跨 HLA 超型与队列分层的最差群体损失。FairTCR 在经过整理的 VDJdb–IEDB 基准上将平均–最差群体 AUPRC 差距从 0.190（ERM）降低至 0.098，实现了 48.4% 的差距缩减，同时保持了竞争性的平均 AUPRC（0.432 对比 ERM 的 0.431）。按 HLA 分析结果显示，罕见等位基因群体（B*08:01、B*44:02）AUPRC 提升最高可达 0.062 点，直接改善了对代表性不足患者群体的计算预筛查公平性。

## Abstract
Public TCR--pMHC binding databases are heavily skewed toward a handful of well-studied HLA alleles---most prominently HLA-A*02:01, which covers $\sim$45\% of curated records---and toward patients from European-ancestry cohorts. Standard empirical risk minimization (ERM) trained on such data achieves strong pooled accuracy but routinely underperforms on rare alleles and underrepresented cohorts, creating systematic disparities that are invisible in single-metric benchmarks. We introduce \emph{FairTCR}, a group distributionally robust optimization (GDRO) framework that minimizes worst-group loss across HLA supertypes and cohort strata via online exponentiated gradient updates. FairTCR reduces the average--worst-group AUPRC disparity from 0.190 (ERM) to 0.098 on a curated VDJdb--IEDB benchmark, achieving a 48.4\% disparity reduction while maintaining competitive average AUPRC (0.432 vs.\ 0.431 for ERM). Per-HLA analysis shows that rare allele groups (B*08:01, B*44:02) gain up to 0.062 AUPRC points, directly improving the equity of computational pre-screening for underrepresented patient populations.