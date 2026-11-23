# In-context Learning and Induction Heads

← [专题索引](../INDEX.MD) · [arXiv:2209.11895v1](https://arxiv.org/abs/2209.11895v1) · [交互式 HTML 原文](https://transformer-circuits.pub/2022/in-context-learning-and-induction-heads/index.html) · [未改动的 Markdown 全文](full.md)

## 摘要

归纳头通过定位先前与当前前缀相匹配的位置，复制其后继 token（`[A][B] … [A] → [B]`）。作者追踪了 34 个 Transformer，并对小模型做了超过 50,000 次注意力头消融。归纳头的形成与上下文学习指标在训练早期的跃迁同步发生；在小型纯注意力模型中，有强因果证据表明归纳头贡献了大部分上下文学习。对于大型含 MLP 的模型，证据主要来自相关性、示例和跨模型类比。论文中的上下文学习指标比较第 50 和第 500 个 token 的预测损失，不等同于对少样本任务准确率的度量。

### Abstract (original)

“Induction heads” are attention heads that implement a simple algorithm to complete token sequences like [A][B] … [A] → [B]. In this work, we present preliminary and indirect evidence for a hypothesis that induction heads might constitute the mechanism for the majority of all “in-context learning” in large transformer models (i.e. decreasing loss at increasing token indices). We find that induction heads develop at precisely the same point as a sudden sharp increase in in-context learning ability, visible as a bump in the training loss. We present six complementary lines of evidence, arguing that induction heads may be the mechanistic source of general in-context learning in transformer models of any size. For small attention-only models, we present strong, causal evidence; for larger models with MLPs, we present correlational evidence.

以下阅读页沿用源 Markdown 的英文正文和静态图。交互式面板及原始排版见 HTML 原文。

## 概念和方法

- [引言](introduction/introduction.md)
- [上下文学习指标](methods/1-in-context-learning.md)
- [归纳头、前缀匹配与复制](methods/2-induction-heads.md)
- [逐 token 损失和 PCA](methods/3-per-token-loss.md)
- [模型规格与训练设置](methods/4-model-details.md)

## 六条证据

- [证据强弱总览](results/0-evidence-overview.md)
1. [相变与归纳头共现](results/1-phase-change.md)
2. [Smeared-key 架构干预](results/2-architecture.md)
3. [测试时归纳头消融](results/3-ablation.md)
4. [字面复制、翻译与模式匹配](results/4-abstract-behavior.md)
5. [QK 与 OV 电路的机制解释](results/5-mechanistic-plausibility.md)
6. [跨模型规模的连续性](results/6-scaling-continuity.md)

## 模型分析图组

- [图组读法与模型范围](results/7-model-analysis.md)
- [小型纯注意力 Transformer](results/8-attention-only.md)
- [小型含 MLP Transformer](results/9-small-mlp.md)
- [大规模 Transformer](results/10-full-scale.md)
- [架构对照与更换训练数据](results/11-controls.md)

## 正文图表

- 方法图：[归纳头](figures/figure-1-induction.md) · [逐 token 损失 PCA 流程](figures/figure-2-loss-pca-workflow.md)
- 相变图：[上下文学习跃迁](figures/figure-3-phase-change.md) · [损失对位置的导数](figures/figure-4-loss-by-position.md) · [前缀匹配](figures/figure-5-prefix-matching.md) · [训练曲线](figures/figure-6-training-loss.md) · [PCA](figures/figure-7-loss-pca.md) · [示例 token](figures/figure-8-token-examples.md)
- 干预和案例：[Smeared-key](figures/figure-9-smeared-key.md) · [消融](figures/figure-10-ablation.md) · [字面复制](figures/figure-11-literal-copying.md) · [翻译](figures/figure-12-translation.md) · [抽象模式匹配](figures/figure-13-pattern-matching.md) · [QK／OV 电路](figures/figure-14-qk-ov-circuit.md)
- 证据强度表：[总表](tables/table-1-evidence-summary.md) · [论据 1](tables/table-2-co-occurrence.md) · [论据 2](tables/table-4-architecture.md) · [论据 3](tables/table-5-ablation.md) · [论据 4](tables/table-6-abstract-behavior.md) · [论据 5](tables/table-8-mechanistic.md) · [论据 6](tables/table-9-scaling.md)
- 其余表格：[示例后继 token](tables/table-3-token-examples.md) · [三个归纳头的评分](tables/table-7-example-heads.md) · [大规模模型规格](tables/table-10-model-properties.md)

## 讨论、附录与文献

- [未解释的现象](discussion/1-unexplained-curiosities.md) · [讨论](discussion/2-discussion.md) · [相关工作](discussion/3-related-work.md)
- [归纳头的层位置](appendix/1-head-location.md) · [分数分布与指标校验](appendix/2-score-distributions.md) · [数据采集和消融流程](appendix/3-data-collection.md) · [度量及归因分析](appendix/4-analyses.md)
- [参考文献](references/references.md) · [评议、复现与更新](back-matter/1-comments-replications.md) · [脚注](back-matter/2-footnotes.md) · [致谢与作者贡献](back-matter/3-contributions.md)
- [作者与引用信息](front-matter/authors-and-citation.md) · [元数据](_meta.md)
