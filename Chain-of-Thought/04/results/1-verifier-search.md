> [返回论文索引](../INDEX.MD) · §5.3

# PRM 搜索：收益取决于难度和预算

低生成预算时，束搜索优于加权 best-of-N。随预算增加优势缩小，有时反转；同预算下 lookahead 通常更弱。扫描了束宽 4 或 $\sqrt N$ 与 0/1/3 步前瞻（不是所有组合都覆盖），最大预算 256。

| 难度桶 | 观察 |
|---|---|
| 1–2 | 高预算束搜索可能劣化，best-of-N 较稳；模型会找到不必要的重复末步骤或过短路径，提示过度优化 PRM。 |
| 3–4 | 束搜索相对 best-of-N 更好；导向正确路径的收益高于只做独立采样。 |
| 5 | 测试的策略都没有显著进展。 |

分桶选择搜索配置后，低预算下 16 次生成可接近 64 次 best-of-N 的效果（接近 4 倍预算差）。预算提高时，预测难度的收益减弱，oracle 分桶的收益更持续。

[总览图](../figures/figure-1-overview.md) · [分难度图](../figures/figure-3-search-difficulty.md) · [自适应搜索曲线](../figures/figure-4-optimal-search.md) · [预测难度](../figures/figure-12-predicted-search.md)
