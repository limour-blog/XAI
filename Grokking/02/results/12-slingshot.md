⬅️ 返回 [../INDEX.MD](../INDEX.MD) · 所属：附录 D.2 · The slingshot mechanism

# Slingshot 不是延迟泛化的必要步骤

**Slingshot 对照。** 两层模型常出现这种优化波动，降低损失计算精度可在单层模型里诱发类似现象，但许多带权重衰减的单层模型没有 slingshot 也会 grok。作者把自适应优化器与不同尺度梯度的相互作用视为可能原因，不把 slingshot 当作必要步骤。

## 关联章节与图表

- [种子、样本占比、深度和模数的对照](../results/10-other-training-runs.md)
- [图 23 · 两层模型的排除损失](../figures/figure-23-two-layer-excluded-loss.md)
