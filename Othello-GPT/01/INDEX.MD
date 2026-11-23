# Emergent world representations: Exploring a sequence model trained on a synthetic task

> **论文 01 · 渐进式披露 Level 1** · [合集索引](../INDEX.MD) · [连续阅读版](full.md) · [元数据](_meta.md)

## 速览

| 项目 | 内容 |
|---|---|
| 作者 | Kenneth Li, Aspen K. Hopkins, David Bau, Fernanda Viégas, Hanspeter Pfister, Martin Wattenberg |
| 版本 | ICLR 2023 · [arXiv:2210.13382v5](https://arxiv.org/abs/2210.13382v5) |
| 任务 | 只看黑白棋落子序列，自回归预测下一步 |
| 证据 | 合法落子评估、棋盘状态探针、反事实激活干预、潜在显著性图 |

## Abstract

Language models show a surprising range of capabilities, but the source of their apparent competence is unclear. Do these networks just memorize a collection of surface statistics, or do they rely on internal representations of the process that generates the sequences they see? We investigate this question in a synthetic setting by applying a variant of the GPT model to the task of predicting legal moves in a simple board game, Othello. Although the network has no a priori knowledge of the game or its rules, we uncover evidence of an emergent nonlinear internal representation of the board state. Interventional experiments indicate this representation can be used to control the output of the network. By leveraging these intervention techniques, we produce “latent saliency maps” that help explain predictions. [Code](https://github.com/likenneth/othello_world)

## 核心发现

- [合法落子](results/1-legal-moves.md)：合成训练的 top-1 非法率为 **0.01%**；排除整个 C5 开局分支后，在该分支上的非法率为 **0.02%**。
- [棋盘解码](results/3-nonlinear-probes.md)：对黑／白／空标签，合成模型的线性探针最低错误率 **20.4%**，两层 MLP 最低 **1.7%**。比较针对论文所用的标签和探针，不排除其他状态编码下的线性读出。
- [因果干预](results/4-causal-role.md)：改写一个棋格的内部状态后，天然／非天然局面的平均错误数分别从 **2.68 / 2.59** 降到 **0.12 / 0.06**。
- [潜在显著性图](results/5-latent-saliency.md)：合成训练主要强调合法性相关棋格，锦标赛训练也强调其他棋格。

## 章节导航（Level 2–3）

### 作者与来源（front-matter/）

- [Authors and affiliations](front-matter/authors-affiliations.md)

### 引言（introduction/）

- [1. Introduction](introduction/introduction.md)

### 方法（methods/）

- [2–2.1. Language modeling of Othello game transcripts: Datasets](methods/1-datasets.md)
- [2.2. Model and Training](methods/2-model-and-training.md)
- [3. Exploring Internal Representations with Probes](methods/3-probe-setup.md)
- [4–4.1. Validating Probes with Interventional Experiments: Intervention Technique](methods/4-intervention.md)
- [Algorithm 1. Attribution via Intervention on Othello-GPT](methods/5-latent-saliency-algorithm.md)

### 结果（results/）

- [2.3. Othello-GPT Usually Predicts Legal Moves](results/1-legal-moves.md)
- [3.1. Linear Probes Have High Error Rates](results/2-linear-probes.md)
- [3.2. Nonlinear Probes Have Lower Error Rates](results/3-nonlinear-probes.md)
- [4.2. Evidence for a Causal Role for the Representation](results/4-causal-role.md)
- [5. Latent Saliency Maps: Attribution via Intervention](results/5-latent-saliency.md)

### 表格（tables/）

- [Table 1. Linear probe error rates](tables/table-1-linear-probe-errors.md)
- [Table 2. Nonlinear probe error rates](tables/table-2-nonlinear-probe-errors.md)
- [Table 3. Regularization weight sweep](tables/table-3-beta-sweep.md)
- [Table 4. Linear probe error standard deviations](tables/table-4-linear-standard-deviations.md)
- [Table 5. Nonlinear probe error standard deviations](tables/table-5-nonlinear-standard-deviations.md)

### 插图（figures/）

- [Figure 1. Othello rules](figures/figure-1-othello-rules.md)
- [Figure 2. Counterfactual board intervention](figures/figure-2-intervention-scheme.md)
- [Figure 3. Intervention errors by starting layer](figures/figure-3-intervention-errors.md)
- [Figure 4. Latent saliency maps](figures/figure-4-latent-saliency.md)
- [Figure 5. Geometry of probe weights](figures/figure-5-probe-geometry.md)
- [Figure 6. Probe capacity, layer, and game progression](figures/figure-6-probe-capacity.md)
- [Figure 7. Counterfactual move probability heatmaps](figures/figure-7-counterfactual-heatmaps.md)
- [Figure 8. Board states before and after each layerwise edit](figures/figure-8-layerwise-probe-interaction.md)
- [Figure 9. Intervention F₁ scores](figures/figure-9-intervention-f1.md)
- [Figure 10. Intervention KL divergence](figures/figure-10-intervention-kl.md)

### 讨论与结论（discussion/）

- [6. Related work](discussion/related-work.md)
- [7. Conclusion](discussion/conclusions.md)

### 附录（appendix/）

- [A. Visualizing the Geometry of Probes](appendix/a-probe-geometry.md)
- [B. Ablation on Nonlinear Probe Accuracies](appendix/b-probe-capacity.md)
- [C. Prediction heatmaps of counterfactual board states](appendix/c-counterfactual-heatmaps.md)
- [D. Inter-probe Interaction](appendix/d-inter-probe-interaction.md)
- [E. Discussion of Latent Saliency Maps](appendix/e-saliency-limitations.md)
- [F. Alternative Metrics for the Intervention Experiment](appendix/f-alternative-metrics.md)
- [G. Ablations on Intervention Hyper-parameters](appendix/g-intervention-hyperparameters.md)
- [H. Standard Deviation of Probe Accuracy](appendix/h-probe-standard-deviations.md)

### 文末声明（back-matter/）

- [Acknowledgments](back-matter/acknowledgments.md)

### 参考文献（references/）

- [References](references/references.md)
