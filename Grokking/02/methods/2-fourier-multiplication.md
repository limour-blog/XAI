⬅️ 返回 [../INDEX.MD](../INDEX.MD) · 所属：§3.1 · The Fourier multiplication algorithm

# 用旋转计算模加法

设 $P$ 为质数，$w_k=2\pi k/P$。对每个使用的频率 $k$，嵌入把输入 $x$ 表示为 $(\cos(w_kx),\sin(w_kx))$。复数写法是 $e^{iw_kx}$；组合 $a$、$b$ 的旋转相当于乘这两个复数，这就是「傅里叶乘法」中的乘法。注意力和 MLP 近似实现三角恒等式：

$$
\begin{aligned}
\cos(w_k(a+b)) &= \cos(w_ka)\cos(w_kb)-\sin(w_ka)\sin(w_kb),\\
\sin(w_k(a+b)) &= \sin(w_ka)\cos(w_kb)+\cos(w_ka)\sin(w_kb).
\end{aligned}
$$

输出层对每个候选答案 $c$，用线性组合算 $\cos(w_k(a+b-c))$：

$$
\cos(w_k(a+b-c))=\cos(w_k(a+b))\cos(w_kc)+\sin(w_k(a+b))\sin(w_kc).
$$

最后将多个频率的结果加权求和。正确答案 $c\equiv a+b\pmod P$ 使各项同时达到余弦峰值；其他候选的峰值通常错开。多个频率一起用，能拉开正确答案与最接近干扰项的分数。

## 关联章节与图表

- [多个频率如何拉开答案分差？](../methods/5-constructive-interference.md)
- [单层 Transformer 的残差流与输出公式](../methods/4-transformer-structure.md)
- [图 1 · 模加法的傅里叶乘法电路](../figures/figure-1-fourier-multiplication-circuit.md)
- [图 8 · 叠加余弦以增强正确答案的峰值](../figures/figure-8-constructive-interference.md)
