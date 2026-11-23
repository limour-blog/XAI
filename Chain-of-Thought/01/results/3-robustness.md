> [返回论文索引](../INDEX.MD) · §3.4、附录 A/D

# 提示鲁棒性

另两位作者（B/C）为同样的题独立写步骤，A 另写简洁版。还用 GSM8K 训练集独立采样 3 组、每组 8 个示例（不超过 60 token、至多两步），并将同一组用于四项算术任务。LaMDA 137B 在 GSM8K 上的替代提示为 11.1%–17.6%，都高于 6.5% 的直接回答基线。五项数据集还调整了提示数量，对比标准与 CoT；提升大体保留。

仍有提示敏感性：LaMDA 137B 在硬币翻转上，A 的 CoT 为 99.6%，C 为 71.4%；不同示例顺序的波动在这一分类任务上也较大。换语言风格通常不抹去收益，并不意味着可以省略提示评估。

[图 6](../figures/figure-6-robustness.md) · [图 11](../figures/figure-11-shot-count.md) · [算术表](../tables/table-6-arithmetic-ablation.md) · [常识与符号表](../tables/table-7-commonsense-symbolic-ablation.md)
