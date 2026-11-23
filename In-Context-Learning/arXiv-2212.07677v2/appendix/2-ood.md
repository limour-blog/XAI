← [论文索引](../INDEX.MD)

# A.2 分布外测试

每个设置对 10,000 个任务平均。实验改变均匀分布输入的尺度或教师的尺度，也测试以各 $1/3$ 概率选择正态、指数或 Laplace 分布的输入，再乘以 $\alpha$。循环模型和 GD/GD++ 在这些测试中表现尤其类似；更深的不共享权重模型在远离 $\alpha=1$ 时对齐较弱。对于深度 $K>2$ 的模型和对应基线，逐层裁剪 token 到 $[-10,10]$，因此曲线可能趋于平台。

[图 6](../figures/figure-6-ood.md) · [图 7](../figures/figure-7-ten-layers.md) · [图 8](../figures/figure-8-twelve-layers.md)
