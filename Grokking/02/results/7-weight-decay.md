⬅️ 返回 [../INDEX.MD](../INDEX.MD) · 所属：§5.3 · Grokking and weight decay

# 权重衰减和训练数据量的作用

在主模加法配置中，去掉权重衰减后没有观察到 grokking，排除损失也没有明显上升；有些 dropout 设置同样能产生延迟泛化。训练数据足够多时，训练和测试可以同步改善，即使内部仍学到同类算法，也没有先过拟合再泛化的间隔。

## 关联章节与图表

- [种子、样本占比、深度和模数的对照](../results/10-other-training-runs.md)
- [权重衰减、dropout 与 L1 惩罚的对照](../results/11-regularization-controls.md)
- [三个算法任务的有限数据对照](../results/13-other-algorithmic-tasks.md)
- [图 26 · 去掉权重衰减的对照](../figures/figure-26-no-weight-decay.md)
