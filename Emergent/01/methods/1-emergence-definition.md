> [返回论文索引](../INDEX.MD) · §2

# 涌现的定义与尺度

> An ability is emergent if it is not present in smaller models but is present in larger models.

操作性判据是：所测下游分数先近随机，后在某一观测规模明显超随机。作者将这一形状与相变类比，并指出仅外推小模型的下游分数不能直接预测大模型结果；这不是对内部机制存在不连续性的证明。对提示或微调策略，判据改为相对于无该策略的基线，收益由无或负转为正。

- 主坐标用训练 FLOPs，[附录](../appendix/5-parameter-scaling.md)还提供参数量坐标。密集模型家族中两者往往相关，训练数据规模同样重要，但一些家族对各模型规模使用固定数据量。
- Chinchilla 参数约为 Gopher 的四分之一却使用相近训练算力；稀疏专家混合的总参数量也不能和密集模型直接换算。见[模型明细](../tables/table-2-model-details.md)。
- 数据量与质量、训练配方和架构都影响首次观测的位置。本文报告的是示例，不给出某能力不可逾越的最小规模。
