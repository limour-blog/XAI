> [返回论文索引](../INDEX.MD) · §6.2

# 顺序修订与并行探索

顺序修订每一步的 pass@1 整体提高，超过训练所见的 4 次修订仍可改善。论文用每题 4 条长度为 64 的轨迹估计。直接取最后一次会丢掉好答案：朴素修订将约 38% 的正确答案改错；用 ORM 或多数投票选答案时，纯顺序比同预算的纯并行略好。

并行探索新解法，修订在已有思路上局部搜索。固定预算改变比例，可得到最优组合；难度分组显示容易题更适合顺序，较难题往往需两者混合。在高预算下，纯并行趋于平台；分桶自适应（oracle 或预测）以 64 次采样可超过 256 次纯并行 best-of-N。这个预算对比不包括难度分桶开销。

[总览图](../figures/figure-1-overview.md) · [轨迹和 pass@1](../figures/figure-6-revision-pass1.md) · [比例图](../figures/figure-7-revision-ratios.md) · [自适应修订](../figures/figure-8-optimal-revisions.md) · [多数投票](../figures/figure-10-majority.md) · [预测难度](../figures/figure-11-predicted-revisions.md)
