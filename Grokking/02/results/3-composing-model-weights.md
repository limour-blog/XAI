⬅️ 返回 [../INDEX.MD](../INDEX.MD) · 所属：§4.2 · Mechanistic evidence: composing model weights

# 读出模型权重里的三角恒等式

**权重读出的量符合恒等式。** 忽略 MLP 旁路后，$W_L=W_UW_{out}$ 把 MLP 激活映射到输出 logits。$W_L$ 能用五对正弦和余弦方向逼近，残差的 Frobenius 范数不到原矩阵的 0.55%。在这十个方向上读出的 MLP 信号，与对应的 $\cos(w_k(a+b))$ 或 $\sin(w_k(a+b))$ 相符；方差解释比例为 93.2%–98.2%。再用五个 $\cos(w_k(a+b-c))$ 项拟合全部 logits，可解释约 95% 的方差。

## 关联章节与图表

- [表 1 · MLP 激活在关键读出方向的傅里叶分量](../tables/table-1-mlp-fourier-projections.md)
- [图 3 · 嵌入与读出权重的频域分量](../figures/figure-3-embedding-fourier-components.md)
