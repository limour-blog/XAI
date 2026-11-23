⬅️ 返回 [../INDEX.MD](../INDEX.MD) · 所属：§5.1 · Progress measures

# 如何计算限制损失和排除损失

在每个检查点，把每个候选 $c$ 的 logits 看成定义在 $(a,b)$ 网格上的函数，沿两个输入轴做二维 DFT。修改频域分量，再逆变换回 logits 并计算交叉熵。

## 关联章节与图表

- [进度指标的定义和读法](../tables/table-4-progress-measures.md)
- [记忆、电路形成与清理](../results/6-training-phases.md)
- [图 7 · 进度指标与训练阶段](../figures/figure-7-training-progress-measures.md)
