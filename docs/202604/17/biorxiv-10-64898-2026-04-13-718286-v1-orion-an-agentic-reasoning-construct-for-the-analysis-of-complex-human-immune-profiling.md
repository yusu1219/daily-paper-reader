---
title: "ORION: An agentic reasoning construct for the analysis of complex human immune profiling"
title_zh: ORION：用于复杂人类免疫组分析的智能推理框架
authors: "Dayao, M. T., Kim, K., Khor, B., Jaech, A., van Opheusden, B., Bodansky, A., DeRisi, J."
date: 2026-04-16
pdf: "https://www.biorxiv.org/content/10.64898/2026.04.13.718286v1.full.pdf"
tags: ["query:gentcr"]
score: 7.0
evidence: 使用具备推理能力的大语言模型对复杂免疫分析数据进行端到端分析的多智能体框架
tldr: 该研究提出ORION系统，通过多智能体框架结合大语言模型，用于复杂免疫组学数据的自动解析。ORION整合统计分析、机器学习及文献检索，可在数小时内完成原需数月的蛋白质组抗体剖析，大幅提升数据解释效率。
source: biorxiv
selection_source: fresh_fetch
figures_json: "[{\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-04-13-718286-v1/fig-001.webp\", \"caption\": \"Figure 1. ORION multi-agent workflow architecture. ORION orchestrates end-to-end PhIP-82 seq analysis through three specialized agents (a Main Analysis Agent, a Literature Agent, and a 83 Supervisor Agent/orchestrator) operating in a constrained Plan → Execute → Verify loop that 84 enforces reproducibility and auditability through persisted, machine-readable intermediate 85\", \"page\": 3, \"index\": 1, \"width\": 1039, \"height\": 581}]"
motivation: 高维生物数据生成速度远超其解释能力，免疫组学分析亟需高效自动化方法。
method: 研究团队开发了基于大语言模型的多智能体分析框架，融合统计和文献推理实现端到端免疫数据解析。
result: ORION在APS-1和唐氏综合征数据集上实现了高准确度的自动抗体特征识别与新靶点预测。
conclusion: ORION显著压缩免疫数据分析周期，为科学家专注于生物机制研究提供新途径。
---

## 摘要
生成高维生物数据集的能力已经超越了对其进行解释的能力。诸如噬菌体免疫沉淀及测序（PhIP-seq）等技术能够在蛋白质组尺度上分析抗体库，但将数千个富集肽段解释为机制性假设仍是一个劳动密集型瓶颈，需要专家综合统计学、文献和领域知识。在此，我们描述了 ORION（Omics Reasoning & Interpretation Orchestrator），一个利用具备推理能力的大型语言模型来执行复杂免疫分析数据端到端解析的多代理框架。ORION 将统计分析、机器学习和自动化文献综述集成到一个结构化工作流程中，产生可复现且完全可追溯的结果。应用于来自自身免疫性多腺体综合征1型（APS-1）的已发表 PhIP-seq 数据集时，ORION 在大约两小时内恢复了经典的自身抗体特征，几乎重现了一个最初需要一到两个月人工分析的过程。为了测试其在未见数据上的假设生成能力，我们将 ORION 应用于来自唐氏综合征个体的一个新 PhIP-seq 数据集，对该数据尚无蛋白质组级自身抗体参考。ORION 以高准确度区分了疾病与对照样本，优先识别了候选自身抗体靶点，并将其组织成跨越免疫、肠道和神经程序的生物学一致组群，生成了可实验验证的假设。这些结果表明，具备行动能力的人工智能系统可以将复杂免疫分析数据的处理时间从数周压缩至数小时，使科学家能够将时间重新投入到基础生物学研究中。

## Abstract
The capacity to generate high-dimensional biological datasets has outpaced the ability to interpret them. Technologies such as phage immunoprecipitation and sequencing (PhIP-seq) enable proteome-scale profiling of antibody repertoires, but interpreting thousands of enriched peptides into mechanistic hypotheses remains a labor-intensive bottleneck requiring expert synthesis of statistics, literature, and domain knowledge. Here we describe ORION (Omics Reasoning & Interpretation Orchestrator), a multi-agent framework that uses reasoning-capable large language models to perform end-to-end analysis of complex immune profiling data. ORION integrates statistical analysis, machine learning, and automated literature review into a single structured workflow, producing results that are reproducible and fully traceable. Applied to a published PhIP-seq dataset from autoimmune polyendocrine syndrome type 1 (APS-1), ORION recovered the canonical autoantibody signature in approximately two hours, closely recapitulating an analysis that originally required one to two months of manual effort. To test hypothesis-generation capacity on previously unseen data, we applied ORION to a novel PhIP-seq dataset from individuals with Down syndrome, for which no proteome-wide autoantibody reference exists. ORION distinguished disease from control samples with high accuracy, prioritized candidate autoantibody targets, and organized them into biologically coherent groups spanning immune, gut, and neuronal programs, generating testable hypotheses for experimental follow-up. These results demonstrate that agentic AI systems can compress the analysis of complex immune profiling data from weeks to hours, allowing scientists to redirect their time toward the fundamental biology.