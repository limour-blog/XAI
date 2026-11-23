← [论文索引](../INDEX.MD)

# A.11 训练相变

单头在某些种子下会长时间停滞、然后突然降至一步 GD 的损失。作者分别用 10 个种子比较单头和双头，双头收敛更快、更稳定。把含 MLP 的单个 Transformer 块限制在 8,192 个训练任务上，在精细调整学习率和批大小后，测试误差先上升再骤降至接近 GD 基线（约 0.2），出现类似 grokking 的现象。

[图 15](../figures/figure-15-phase-transitions.md) · [单层结果](../results/1-single-layer.md)
