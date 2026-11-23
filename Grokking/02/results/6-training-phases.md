⬅️ 返回 [../INDEX.MD](../INDEX.MD) · 所属：§5.2 · Phases of grokking

# 记忆、电路形成与清理

用限制损失衡量泛化电路能否独立解题，用排除损失衡量移除电路后模型还能否拟合训练集。两者的变化把主实验分成三个阶段。

这些指标是利用最终模型的关键频率**回看**训练进程，不等于能事先预测任意模型何时跃升。

## 关联章节与图表

- [如何计算限制损失和排除损失](../methods/3-fourier-progress-measures.md)
- [记忆、电路形成与清理的观测对照](../tables/table-5-training-phases.md)
- [图 7 · 进度指标与训练阶段](../figures/figure-7-training-progress-measures.md)
- [图 13 · 只保留关键频率后的准确率](../figures/figure-13-restricted-accuracy.md)
- [图 14 · 余弦项系数随训练的变化](../figures/figure-14-cosine-coefficients.md)
- [图 15 · 逐一排除关键频率的准确率与损失](../figures/figure-15-excluding-key-frequencies.md)
