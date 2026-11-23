← [论文索引](../INDEX.MD)

# A.9 线性注意力、softmax 和 LayerNorm

训练所得单头 softmax 层未能达到线性 GD 的损失。近零展开 $\exp(s_i)\approx1+s_i$ 表明 softmax 会引入一个常量项和依赖上下文的归一化。作者提出用两个头做差：在适当吸收归一化且值投影匹配的近似下，常量抵消，剩余项与 $x_i^\top(W_{1,KQ}-W_{2,KQ})x_j$ 成正比。实验里，双头显著改善损失和对齐，带有效学习率缩放的权重乘积也显示非对角项近似抵消，但损失不完全匹配。引入 LayerNorm 的一层及两层模型同样没有达到对应 GD 的损失。

[图 11：双头权重](../figures/figure-11-softmax-weights.md) · [图 12：softmax](../figures/figure-12-softmax.md) · [图 14：LayerNorm](../figures/figure-14-layernorm.md)
