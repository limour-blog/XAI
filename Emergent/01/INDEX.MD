# Emergent Abilities of Large Language Models

> [合集索引](../INDEX.MD) · Level 1 · TMLR 2022 · [arXiv:2206.07682v2](https://arxiv.org/abs/2206.07682v2) · [OpenReview](https://openreview.net/forum?id=yzkSU5zdwD) · [主 TeX](../../TeX/Emergent/arXiv-2206.07682v2/main.tex)

| 项目 | 速览 |
|---|---|
| 研究类型 | 文献综述，附 BIG-Bench 与 MMLU 的补充分析 |
| 规模坐标 | 训练 FLOPs、参数量；另看 WikiText103 困惑度 |
| 核心发现 | 5 个模型家族的 8 个少样本实例，以及 4 个增强策略案例；观察规模并非固定门槛 |

## 摘要（Abstract）

Scaling up language models has been shown to predictably improve performance and sample efficiency on a wide range of downstream tasks. This paper instead discusses an unpredictable phenomenon that we refer to as *emergent abilities* of large language models. We consider an ability to be emergent if it is not present in smaller models but is present in larger models. Thus, emergent abilities cannot be predicted simply by extrapolating the performance of smaller models. The existence of such emergence raises the question of whether additional scaling could potentially further expand the range of capabilities of language models.

## 关键结论

- 少样本能力相对随机基线定义；增强策略相对不采用该策略的基线定义。这两种比较不可混同。
- LaMDA 的 6 个 BIG-Bench 案例中，下游评分仍接近随机时，目标的交叉熵已改善；论文没有据此建立可预测阈值的模型。
- PaLM 62B 在 14 个任务超过随机，而 GPT-3 175B 和 LaMDA 137B 近似随机；参数量并不是唯一解释变量。

## 章节导航

- 前置信息：[作者与机构](front-matter/authors-affiliations.md) · [元数据](_meta.md)
- 正文：[§1 引言](introduction/introduction.md) · [§2 定义与规模](methods/1-emergence-definition.md) · [§3 少样本任务](results/1-few-shot-tasks.md) · [§4 增强提示与微调](results/2-augmented-prompting.md) · [§5 讨论](discussion/discussion.md) · [§6 结论](discussion/conclusions.md)
- 附录：[A BIG-Bench 交叉熵](appendix/1-big-bench-cross-entropy.md) · [A 生成指标](appendix/2-generative-metrics.md) · [A 任务关键词](appendix/3-task-keywords.md) · [B MMLU 分层](appendix/4-mmlu-stratification.md) · [C 模型明细](tables/table-2-model-details.md) · [D 参数尺度](appendix/5-parameter-scaling.md) · [E 分类标注](appendix/6-task-annotations.md) · [F PaLM 62B 的 14 项](appendix/7-palm-62b.md)
- 表：[表 1 涌现实例与规模](tables/table-1-emergence-scales.md) · [表 2 参数、token、FLOPs](tables/table-2-model-details.md)
- 正文图：[图 1 少样本示意](figures/figure-1-few-shot-example.md) · [图 2 八个实例](figures/figure-2-few-shot-flops.md) · [图 3 四种增强策略](figures/figure-3-interventions-flops.md) · [图 4 MMLU 与困惑度](figures/figure-4-mmlu-scale.md)
- 附录图：[图 5 生成交叉熵](figures/figure-5-generative-loss.md) · [图 6 分类交叉熵](figures/figure-6-classification-loss.md) · [图 7 替代生成指标](figures/figure-7-generative-metrics.md) · [图 8 关键词分类](figures/figure-8-task-keywords.md) · [图 9 最大与次大模型](figures/figure-9-mmlu-summary.md) · [图 10 MMLU 分层曲线](figures/figure-10-mmlu-strata.md) · [图 11 少样本参数尺度](figures/figure-11-few-shot-params.md) · [图 12 增强策略参数尺度](figures/figure-12-interventions-params.md) · [图 13 通用模型超越专用模型](figures/figure-13-general-purpose-sota.md)
- 文末：[影响声明与致谢](back-matter/impact-and-acknowledgments.md) · [参考文献](references/references.md)
