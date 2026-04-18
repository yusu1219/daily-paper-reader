---
title: "FairTCR: Equity-Aware TCR--pMHC Binding Prediction\\\\Across HLA Alleles and Cohort Strata"
title_zh: FairTCR：面向公平性的跨HLA等位基因与队列层次的TCR–pMHC结合预测
authors: "Nowak, P., Kowalski, J., Lewandowski, T."
date: 2026-04-17
pdf: "https://www.biorxiv.org/content/10.64898/2026.04.14.718511v1.full.pdf"
tags: ["query:gentcr"]
score: 7.0
evidence: 跨HLA等位基因的TCR-pMHC结合预测与优化
tldr: 本研究提出了FairTCR模型，针对TCR–pMHC结合数据集中HLA等位基因和群体偏倚问题，采用群体分布鲁棒优化(GDRO)方法，通过最小化最差群体损失提升模型公平性，实验表明FairTCR在保持平均精度的同时显著降低了不同HLA群体间的性能差距。
source: biorxiv
selection_source: fresh_fetch
figures_json: "[{\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-04-14-718511-v1/fig-001.webp\", \"caption\": \"TABLE II DATASET AND SPLIT SUMMARY (ALL HLA SUPERTYPES COMBINED).\", \"page\": 3, \"index\": 1, \"width\": 529, \"height\": 352}]"
motivation: 现有TCR–pMHC结合数据存在HLA等位基因和人群分布不均，导致传统模型在少数群体上预测性能不足。
method: 采用群体分布鲁棒优化结合指数梯度更新方法以最小化最差群体损失。
result: FairTCR显著减少了TCR–pMHC结合预测中不同HLA等位基因和队列群体间的性能差异。
conclusion: FairTCR在保障预测性能的同时显著提升了模型对稀有HLA等位基因和少数群体的公平性。
---

## 摘要
公共的TCR–pMHC结合数据库高度偏向于少数几个研究较充分的HLA等位基因——尤其是HLA-A*02:01，其占据约45%的整理记录——以及来自欧洲血统队列的患者。在此类数据上训练的标准经验风险最小化（ERM）方法在总体准确率上表现出色，但在罕见等位基因和代表性不足的队列上常常表现欠佳，导致系统性差异，而这类差异在单一指标基准中无法察觉。我们提出了\emph{FairTCR}，一种群体分布鲁棒优化（GDRO）框架，通过在线指数梯度更新在HLA超型和队列层次上最小化最差群体损失。FairTCR在整理的VDJdb–IEDB基准上将平均–最差群体AUPRC差异从0.190（ERM）降低至0.098，实现了48.4%的不平等差异减少，同时保持了竞争性的平均AUPRC（0.432对ERM的0.431）。对每种HLA的分析显示，罕见等位基因群体（如B*08:01、B*44:02）AUPRC提升最多达0.062点，直接改善了针对代表性不足患者群体的计算预筛的公平性。

## Abstract
Public TCR--pMHC binding databases are heavily skewed toward a handful of well-studied HLA alleles---most prominently HLA-A*02:01, which covers $\sim$45\% of curated records---and toward patients from European-ancestry cohorts. Standard empirical risk minimization (ERM) trained on such data achieves strong pooled accuracy but routinely underperforms on rare alleles and underrepresented cohorts, creating systematic disparities that are invisible in single-metric benchmarks. We introduce \emph{FairTCR}, a group distributionally robust optimization (GDRO) framework that minimizes worst-group loss across HLA supertypes and cohort strata via online exponentiated gradient updates. FairTCR reduces the average--worst-group AUPRC disparity from 0.190 (ERM) to 0.098 on a curated VDJdb--IEDB benchmark, achieving a 48.4\% disparity reduction while maintaining competitive average AUPRC (0.432 vs.\ 0.431 for ERM). Per-HLA analysis shows that rare allele groups (B*08:01, B*44:02) gain up to 0.062 AUPRC points, directly improving the equity of computational pre-screening for underrepresented patient populations.