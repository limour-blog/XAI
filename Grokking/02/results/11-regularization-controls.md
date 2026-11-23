⬅️ 返回 [../INDEX.MD](../INDEX.MD) · 所属：附录 D.1 · Regularization and limited data

# 权重衰减、dropout 与 L1 惩罚的对照

**正则化对照。** 主配置去掉权重衰减后没有 grokking，排除损失也没有上升。把权重衰减替换为 MLP dropout，$p=0.2$、$p=0.5$ 的三次运行均观察到 grokking；测试的 $\ell_1$ 惩罚未重现此结果。这是对特定设置的对照，并不要求所有 grokking 都有显式权重衰减。原文附录 D.1 对不同衰减系数列出的时间顺序与该段结论及图注相反，因此这里不采用那组时间作定量比较。

## 关联章节与图表

- [权重衰减和训练数据量的作用](../results/7-weight-decay.md)
- [图 26 · 去掉权重衰减的对照](../figures/figure-26-no-weight-decay.md)
- [图 27 · 两种权重衰减强度的对照](../figures/figure-27-weight-decay-strength.md)
