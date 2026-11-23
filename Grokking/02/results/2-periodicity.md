⬅️ 返回 [../INDEX.MD](../INDEX.MD) · 所属：§4.1 · Suggestive evidence: surprising periodicity

# 嵌入、激活和 logits 的周期性

**周期性。** 对嵌入矩阵 $W_E$ 沿 token 轴做离散傅里叶变换，显著信号集中在少数频率。主实验后续计算实际使用 $k\in\{14,35,41,42,52\}$；注意力权重、神经元激活和 logits 也表现出周期结构。

## 关联章节与图表

- [图 3 · 嵌入与读出权重的频域分量](../figures/figure-3-embedding-fourier-components.md)
- [图 4 · 注意力分数、MLP 激活与 logits 的周期性](../figures/figure-4-periodicity-of-activations.md)
