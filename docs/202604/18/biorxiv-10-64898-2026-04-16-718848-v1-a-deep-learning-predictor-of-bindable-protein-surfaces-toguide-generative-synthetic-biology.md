---
title: A deep learning predictor of bindable protein surfaces toguide generative synthetic biology
title_zh: 用于指导生成式合成生物学的可结合蛋白质表面深度学习预测器
authors: "Almeida-Souza, L."
date: 2026-04-16
pdf: "https://www.biorxiv.org/content/10.64898/2026.04.16.718848v1.full.pdf"
tags: ["query:gentcr"]
score: 7.0
evidence: 用于蛋白质结合剂设计和生成合成生物学的深度学习
tldr: 本研究针对蛋白结合体设计中高计算开销的问题，提出了基于图神经网络的IARA模型，可在秒级预测蛋白表面的可结合区域。实验结果表明IARA能精准识别最佳结合界面，显著降低生成设计的计算需求，推动合成生物学的普及与效率提升。
source: biorxiv
selection_source: fresh_fetch
figures_json: "[{\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-04-16-718848-v1/fig-001.webp\", \"caption\": \"Figure 1 – Building a graph neural network to predict bindable protein regions. a, Dataset generation strategy. b, Residue feature extraction and protein conversion to Graphs. c, Architecture of the neural network used for training. d, IARA scoring.\", \"page\": 3, \"index\": 1, \"width\": 1094, \"height\": 430}]"
motivation: 现有蛋白结合体的生成设计需大量计算资源，阻碍了深度学习在合成生物学中的广泛应用。
method: 该研究提出了IARA，一种基于图神经网络的深度学习结构过滤器，用于快速评估蛋白表面的可结合性。
result: IARA在BindCraft、RFdiffusion和BoltzGen等验证中准确识别了目标蛋白的最佳结合界面，大幅降低计算成本。
conclusion: IARA显著加速了蛋白结合位点预测过程，为生成性合成生物学的广泛应用提供了高效且可扩展的解决方案。
---

## 摘要
生成式机器学习模型的出现已经彻底革新了蛋白质结合体的全新设计（de novo design）。然而，这场革命的广泛应用仍受到计算成本的限制。对于许多靶标而言，结合体设计通常需要在结构空间中进行大量的采样，常常将大量 GPU 时间浪费在不需要或几何上不可行的区域上。在此，我们介绍了 IARA（Interface Analysis and Recognition Architecture），这是一种深度学习图神经网络，旨在作为一种快速的结构筛选器，用于分流蛋白结合体的生成流程。IARA 完全基于针对 RFdiffusion 生成靶标的 BindCraft 轨迹进行训练。凭借仅包含七个残基特征的轻量网络结构，IARA 能在数秒内映射输入蛋白的可设计结合性。在使用 BindCraft、RFdiffusion 和 BoltzGen 进行的验证运行中，IARA 成功识别出几乎所有靶标的最佳结合界面。通过即时定位最高概率的结合位点，IARA 实现了合成生物学的普惠化，大幅减少了成功进行全新结合体生成所需的探索性 GPU 计算。

## Abstract
The advent of generative machine learning models has revolutionized de novo design of protein binders. However, the wide adoption of this revolution is bottlenecked by computational cost. For many targets, binder design commonly requires computationally intensive sampling across structures, often wasting days of GPU time on unwanted or geometrically inviable regions. Here, IARA (Interface Analysis and Recognition Architecture) is introduced, a deep learning Graph Neural Network designed as a rapid structural filter to triage protein binder generative pipelines. IARA is trained entirely on BindCraft trajectories generated against s RFdiffusion-generated targets. Based on a slim network with only seven residue features, IARA maps the binder designability of input proteins in a matter of seconds. On validation runs using BindCraft, RFdiffusion and BoltzGen, IARA successfully identified the optimal binding interface for practically all targets. By instantly pinpointing the highest-probability binding pockets, IARA democratizes synthetic biology, drastically reducing the exploratory GPU compute required for successful de novo binder generation.