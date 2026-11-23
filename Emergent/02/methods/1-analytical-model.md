> [返回论文索引](../INDEX.MD) · §2 · [图 2](../figures/figure-2-analytical-model.md)

# 平滑的单 token 进步如何产生尖锐曲线

设参数量 $N>0$，举例取 $\mathcal L_{CE}(N)=(N/c)^\alpha$，$c>0,\alpha<0$。该特定幂律只是示意。词表 $V$ 上的交叉熵为 $-\sum_{v\in V}p(v)\log\hat p_N(v)$；单个目标 $v^*$ 的 one-hot 情况给出 $p_N=\hat p_N(v^*)=\exp(-\mathcal L_{CE}(N))$。

若长度为 $L$ 的序列中 token 正确事件近似独立、具有同一成功率，则

$$\operatorname{Accuracy}(N)\approx p_N^L=\exp[-L(N/c)^\alpha].$$

忽略插入／删除，编辑距离近似替换计数：

$$\operatorname{TokenEditDistance}(N)\approx L(1-p_N).$$

整串准确率随长度按几何方式下降，可能长时间落在可分辨范围以下；替换计数随长度近似线性。实际自回归误差不独立，这只是定性近似。选择题的 argmax 在排序交换时跳变；Brier Score 连续衡量预测概率与结果的差异。若测试集有 $m$ 个样本，序列准确率的最小计数增量为 $1/m$；小模型的测试样本不足及大模型规模点采样稀疏都会放大表观跃升。

[原文 §2](../../../TeX/Emergent/arXiv-2304.15004v2/02_analytical_model.tex) · [附录：顺序数据上的近似](../appendix/1-sequence-metrics.md)
