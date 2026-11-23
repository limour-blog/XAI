← [论文索引](../INDEX.MD) · [训练相变](../appendix/11-phase-transitions.md) · [单层结果](../results/1-single-layer.md)

# 图 15 · 训练相变与 grokking 式泛化

单头在部分种子下停滞后才收敛；双头更稳定。固定在 8,192 个任务上训练带 MLP 的单块模型时，测试损失在上升后骤降。

![单头，10 个种子](../images/grokking/1head_10seeds.png)

![双头，10 个种子](../images/grokking/2heads_10seeds.png)

![固定数据时的泛化跃迁](../images/grokking/grokking.png)
