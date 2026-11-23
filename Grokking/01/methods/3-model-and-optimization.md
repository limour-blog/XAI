⬅️ 返回 [../INDEX.MD](../INDEX.MD) · 所属：附录 A.1 · Model and optimization

# 模型与优化配置

所有实验采用两层 decoder-only Transformer。



消融比较了全批量 Adam、普通 Adam、全批量 Adam 加高斯更新噪声、残差 dropout 0.1、向零衰减、向初始化值衰减、学习率 $3\times10^{-4}$ 或 $3\times10^{-3}$，以及训练时给权重加标准差 0.01 的高斯噪声。

## 关联章节与图表

- [二元运算任务与评估](../methods/1-binary-operation-task.md)
- [模型和训练超参数](../tables/table-2-training-configuration.md)
