> [返回论文索引](../INDEX.MD) · §4 · [图 5](../figures/figure-5-big-bench-metrics.md)

# BIG-Bench：跃升集中于哪些指标？

分析单位为任务—指标—模型家族三元组。按规模由小到大排列分数 $y_i$，BIG-Bench 的涌现分数为

$$E=\frac{\operatorname{sign}(\arg\max_i y_i-\arg\min_i y_i)(\max_i y_i-\min_i y_i)}{\sqrt{\operatorname{median}_{i>1}\big[(y_i-y_{i-1})^2\big]}}.$$

大分数表示可能存在跃升，不等于实质涌现。39 种首选指标中，按该分数最多 5 种出现候选；人工标注中为 4/39。Multiple Choice Grade 与 Exact String Match 合计覆盖超过 92% 的人工标注案例。其他少数指标含 ROUGE-L-Sum；其特性另见[附录](../appendix/1-sequence-metrics.md)。

同一任务常有多种评分，集中度提供度量依赖的线索，不是独立随机分配指标的因果实验。[逐任务 LaMDA 比较](4-lamda-brier.md) · [原文](../../../TeX/Emergent/arXiv-2304.15004v2/04_emergent_paper.tex)
