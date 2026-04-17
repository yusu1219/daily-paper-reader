---
title: "Optimizing Protein Tokenization: Reduced Amino Acid Alphabets for Efficient and Accurate Protein Language Models"
title_zh: 优化蛋白质分词：用于高效且准确的蛋白质语言模型的简化氨基酸字母表
authors: "Rannon, E., Burstein, D."
date: 2026-04-12
pdf: "https://www.biorxiv.org/content/10.64898/2026.02.08.701987v2.full.pdf"
tags: ["query:gentcr"]
score: 7.0
evidence: 优化用于序列生成和建模的蛋白质语言模型
tldr: 本研究针对蛋白质语言模型中使用20种氨基酸编码导致输入长、计算代价高的问题，探索将物理化学性质相似的氨基酸分组形成简化字母表，并结合子词级BPE分词方法进行优化。研究通过在RoBERTa框架上重新训练模型，系统评估多种简化字母表对下游任务的影响，结果显示序列显著缩短、训练推理更高效，且性能几乎不下降甚至在部分任务上提升。
source: biorxiv
selection_source: fresh_fetch
figures_json: "[{\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-02-08-701987-v2/fig-001.webp\", \"caption\": \"Table 2. The ten most frequent tokens of each ProtBERTa (PBa) model observed in the tokenizer evaluation set.\", \"page\": 4, \"index\": 1, \"width\": 500, \"height\": 402}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-02-08-701987-v2/fig-002.webp\", \"caption\": \"Fig. 2. The performance of the different ProtBERTa models on primary metrics of the DGEB benchmark. The metrics descriptions are detailed in Supplementary Table 2.\", \"page\": 4, \"index\": 2, \"width\": 485, \"height\": 481}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-02-08-701987-v2/fig-003.webp\", \"caption\": \"Fig. 3. Zero-shot performance of the five ProtBERTa models on the task of homology detection. Left: ROC curves; right: precision–recall curves. The area under the curve score ± the standard error is noted in parentheses.\", \"page\": 4, \"index\": 3, \"width\": 509, \"height\": 256}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-02-08-701987-v2/fig-004.webp\", \"caption\": \"Fig. 4. Performance of kNN classifiers using ProtBERTa pre-trained embeddings on the task of signal peptide classification. Left: ROC curves; right: precision–recall curves. The area under the curve score ± the standard error is written in parentheses.\", \"page\": 5, \"index\": 4, \"width\": 493, \"height\": 250}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-02-08-701987-v2/fig-005.webp\", \"caption\": \"Fig. 7. Inference run time comparison for the five ProtBERTa models on a variety of downstream tasks. Inference time is measured as a function of the dataset size (in thousands). Error bars represent standard error.\", \"page\": 6, \"index\": 5, \"width\": 498, \"height\": 283}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-02-08-701987-v2/fig-006.webp\", \"caption\": \"Table 1. The amino acid alphabets used in this study and the groups of amino acids represented in their alphabet. The letter representing each group is written in parentheses.\", \"page\": 3, \"index\": 6, \"width\": 498, \"height\": 386}]"
motivation: 标准氨基酸编码导致蛋白质序列过长、模型训练代价高，需寻找更高效的编码方式。
method: 使用多种简化氨基酸字母表结合BPE分词方法，在RoBERTa架构上进行预训练并评估。
result: 实验表明，使用简化字母表显著减少输入序列长度，加快训练和推理速度，并在部分任务上提升准确率。
conclusion: 简化氨基酸字母表结合子词分词能在保持或提升性能的同时显著提高蛋白质语言模型的效率。
---

## 摘要
蛋白质语言模型（pLMs）通常在单个氨基酸水平上对序列进行分词，使用20种氨基酸字母表，这导致输入序列较长并且计算成本较高。诸如 Byte Pair Encoding（BPE）等子词分词方法可以缩短序列长度，但受限于标准氨基酸字母表编码的蛋白质中长序列模式的稀疏性。通过理化性质将氨基酸残基分组的简化氨基酸字母表提供了一种潜在的解决方案，但其与子词分词方法结合使用的性能尚未得到系统研究。在本研究中，我们探讨了在蛋白质语言模型中结合使用简化氨基酸字母表和 BPE 分词的方法。我们基于 RoBERTa 从头预训练了使用多种简化字母表的 pLM，并在多样化的下游任务中对其进行了评估。结果表明，简化字母表能显著缩短输入序列，提升训练和推理速度。这些发现表明，字母表简化可能有助于更有效的子词分词，在仅对预测性能产生微小影响的同时提高效率，并在某些特定任务中甚至提升准确率。

## Abstract
Protein language models (pLMs) typically tokenize sequences at the single-amino-acid level using a 20-residue alphabet, resulting in long input sequences and high computational cost. Sub-word tokenization methods such as Byte Pair Encoding (BPE) can reduce sequence length but are limited by the sparsity of long patterns in proteins encoded by the standard amino acid alphabet. Reduced amino acid alphabets, which group residues by physicochemical properties, offer a potential solution but their performances with sub-word tokenization have not been systematically studied. In this work, we investigate the combined use of reduced amino acid alphabets and BPE tokenization in protein language models. We pre-train RoBERTa-based pLMs de novo using multiple reduced alphabets and evaluate them across diverse downstream tasks. Our results show that reduced alphabets enable substantially shorter input sequences and faster training and inference. These findings suggest that alphabet reduction may facilitate more effective sub-word tokenization, enabling increased efficiency with marginal impact on predictive performance, and for specific tasks even improving accuracy.