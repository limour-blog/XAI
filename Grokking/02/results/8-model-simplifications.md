⬅️ 返回 [../INDEX.MD](../INDEX.MD) · 所属：附录 A.1 · Empirical model simplifications

# 哪些计算路径可以省略？

- 各头给 `=` 自身的平均注意力仅 0.1%–0.4%，消融不影响表现。忽略它以后，对两个位置做 softmax，相当于对两者分数之差取 sigmoid。
- 将 MLP 旁路置零或替换为均值，不改变主模型准确率；损失分别变为 $9.12\times10^{-7}$ 和 $7.25\times10^{-7}$。因此研究主要计算路径时可令 $\operatorname{Logits}\approx W_Lm$，其中 $W_L=W_UW_{out}$。这不意味着注意力或注意力旁路也可忽略：分别置零会将损失推高到 24.3 和 19.1。

## 关联章节与图表

- [单层 Transformer 的残差流与输出公式](../methods/4-transformer-structure.md)
