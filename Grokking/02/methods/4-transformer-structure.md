⬅️ 返回 [../INDEX.MD](../INDEX.MD) · 所属：附录 A · Mathematical structure of the Transformer

# 单层 Transformer 的残差流与输出公式

输入位置 $i$ 的初始残差向量为 $x_i^{(0)}=W_Et_i+p_i$，其中 $t_i$ 是 one-hot token，$p_i$ 是位置嵌入。只在最终的 `=` 位置读取结果。注意力头 $j$ 用等号位置生成查询，用各位置生成键；softmax 得到注意力权重 $A_i^j$，各位置的值通过 OV 映射 $W_O^jW_V^j$ 加到等号位置的残差流。按附录的简写，令 $m$ 为 MLP 的 ReLU 激活，有

$$
\begin{aligned}
x^{(1)} &= x_2^{(0)}+\sum_j W_O^j W_V^j\sum_i A_i^j x_i^{(0)},\\
m &= \operatorname{ReLU}(W_{in}x^{(1)}),\\
\operatorname{Logits} &= W_U\bigl(x^{(1)}+W_{out}m\bigr).
\end{aligned}
$$

## 关联章节与图表

- [用旋转计算模加法](../methods/2-fourier-multiplication.md)
- [哪些计算路径可以省略？](../results/8-model-simplifications.md)
