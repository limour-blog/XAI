# Linear Representations of Sentiment in Large Language Models

> **论文 02 · 渐进式披露 Level 1** · [合集索引](../INDEX.MD) · [连续阅读版](full.md) · [元数据](_meta.md)

## 速览

| 项目 | 内容 |
|---|---|
| 作者 | Curt Tigges, Oskar John Hollinsworth, Atticus Geiger, Neel Nanda |
| 版本 | [arXiv:2310.15154v1](https://arxiv.org/abs/2310.15154v1) · 2023 |
| 任务 | 电影评论续写／分类、多人物情绪预测、自然文本上的词级情感评估 |
| 证据 | 五种方向估计、激活替换与消融、注意力回路、跨数据集验证 |

## Abstract

Sentiment is a pervasive feature in natural language text, yet it is an open question how sentiment is represented within Large Language Models (LLMs). In this study, we reveal that across a range of models, sentiment is represented linearly: a single direction in activation space mostly captures the feature across a range of tasks with one extreme for positive and the other for negative. Through causal interventions, we isolate this direction and show it is causally relevant in both toy tasks and real world datasets such as Stanford Sentiment Treebank. Through this case study we model a thorough investigation of what a single direction means on a broad data distribution.

We further uncover the mechanisms that involve this direction, highlighting the roles of a small subset of attention heads and neurons. Finally, we discover a phenomenon which we term the summarization motif: sentiment is not solely represented on emotionally charged words, but is additionally summarised at intermediate positions without inherent sentiment, such as punctuation and names. We show that in Stanford Sentiment Treebank zero-shot classification, 76% of above-chance classification accuracy is lost when ablating the sentiment direction, nearly half of which (36%) is due to ablating the summarized sentiment direction exclusively at comma positions.

## 核心发现

- [线性情感方向](results/1-direction-comparison.md)：均值差、K-means、逻辑回归、DAS、PCA 得到相近的残差流方向。
- [因果验证](results/3-causal-evaluation.md)：在 Pythia-1.4B 上，用玩具数据训练的 DAS 方向做单层替换，翻转了筛选后 SST 样本中 **53.5%** 的预测。
- [情感汇总](results/5-punctuation-summarization.md)：逗号、句号、重复人名等原本不带情感的 token 可以存储情感供后续读取。
- [SST 消融](results/6-sst-summarization.md)：在 Pythia-2.8B 原本正确分类且含逗号的子集上，全位置消融使准确率从 **100%** 降至 **62%**，仅消融逗号位置降至 **82%**。这分别是高于随机水平的准确率余量的 **76%** 和 **36%**。

## 章节导航（Level 2–3）

### 作者与来源（front-matter/）

- [Authors and affiliations](front-matter/authors-affiliations.md)

### 引言（introduction/）

- [1. Introduction](introduction/introduction.md)

### 方法（methods/）

- [2.1. Datasets and Models](methods/1-datasets-and-models.md)
- [2.2. Finding Directions](methods/2-direction-finding.md)
- [2.3. Causal Interventions](methods/3-causal-interventions.md)

### 结果（results/）

- [3.1. Visualizing and Comparing the Directions](results/1-direction-comparison.md)
- [3.2. Correlational Evaluation](results/2-correlational-evaluation.md)
- [3.3. Causal Evaluation](results/3-causal-evaluation.md)
- [4.1. Circuit Analyses](results/4-circuit-analyses.md)
- [4.2. Exploring and validating summarization behavior in punctuation](results/5-punctuation-summarization.md)
- [4.3. Validating summarization behavior in SST](results/6-sst-summarization.md)

### 表格（tables/）

- [Figure 3 table. Classification accuracy at sentiment activation extremes](tables/table-figure-3-classification-accuracy.md)
- [Figure 5 table. Negation experiment](tables/table-figure-5-negation-experiment.md)
- [Table 1a. Change in logit difference from interventions on attention head value vectors](tables/table-1a-comma-vs-phrase.md)
- [Table 1b. Ratio of logit difference change for periods versus phrases after value patching](tables/table-1b-period-distance.md)

### 插图（figures/）

- [Figure 1. Sentiment projections in varied text](figures/figure-1-sentiment-across-texts.md)
- [Figure 2. Cosine similarity of direction estimates](figures/figure-2-direction-similarities.md)
- [Figure 3. Sentiment activation bins in OpenWebText](figures/figure-3-openwebtext.md)
- [Figure 4. Directional patching in Pythia-1.4B](figures/figure-4-direction-patching.md)
- [Figure 5. Sentiment under negation](figures/figure-5-negation-experiment.md)
- [Figure 6. Directional patching transfer by layer](figures/figure-6-intermediate-layers.md)
- [Figure 7. GPT2-small sentiment circuit](figures/figure-7-gpt2-circuit.md)
- [Figure 8. Value-weighted attention to comma positions](figures/figure-8-comma-attention.md)
- [Figure A.1. PCA of adjectives and verbs](figures/figure-a-1-pca-embeddings.md)
- [Figure A.2. Two-means classification across GPT-2 models](figures/figure-a-2-gpt2-clustering.md)
- [Figure A.3. Activation addition and output sentiment](figures/figure-a-3-activation-addition.md)
- [Figure A.4. English and French sentiment projections](figures/figure-a-4-multilingual.md)
- [Figure A.5. Negation across layers](figures/figure-a-5-negation-layers.md)
- [Figure A.6. DAS subspace dimension sweep](figures/figure-a-6-das-dimensions.md)
- [Figure A.7. Residual and layer-output patching](figures/figure-a-7-gpt2-residual-patching.md)
- [Figure A.8. Heads affected by comma or phrase patching](figures/figure-a-8-comma-phrase-heads.md)
- [Figure A.9. Path patching to summary heads](figures/figure-a-9-comma-path-patching.md)
- [Figure A.10. Neuron output directions and sentiment](figures/figure-a-10-neuron-similarity.md)

### 讨论与结论（discussion/）

- [4.4. The big picture of summarization](discussion/summarization-overview.md)
- [5. Related Work](discussion/related-work.md)
- [6. Conclusion and future work](discussion/conclusions.md)
- [6. Limitations](discussion/limitations.md)

### 附录（appendix/）

- [A.1.1. Clustering](appendix/a1-1-clustering.md)
- [A.1.2. Activation addition](appendix/a1-2-activation-addition.md)
- [A.1.3. Multi-lingual sentiment](appendix/a1-3-multilingual.md)
- [A.1.4. Interpretability of negations](appendix/a1-4-negations.md)
- [A.2. Is sentiment really a hyperplane?](appendix/a2-das-dimensions.md)
- [A.3. Detailed circuit analysis](appendix/a3-detailed-circuits.md)
- [A.4. Additional summarization findings](appendix/a4-additional-summarization.md)
- [A.5. Neurons writing to the sentiment direction in GPT2-small](appendix/a5-neurons.md)
- [A.6. Detailed description of metrics](appendix/a6-metrics.md)
- [A.7. Toy dataset details](appendix/a7-toy-datasets.md)
- [A.8. Glossary](appendix/a8-glossary.md)

### 文末声明（back-matter/）

- [Author Contributions](back-matter/author-contributions.md)
- [Acknowledgments](back-matter/acknowledgments.md)
- [Reproducibility Statement](back-matter/reproducibility.md)

### 参考文献（references/）

- [References](references/references.md)
