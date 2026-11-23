> [返回论文索引](../INDEX.MD) · §2.2

# 电路复杂度术语

布尔电路是由输入变量和逻辑门构成的有向无环图。$\mathsf{SIZE}[T(n)]$ 允许每个输入长度 $n$ 有一个大小 $O(T(n))$ 的电路；电路必须正确判定该长度的全部输入。$\mathsf{P/poly}$ 为多项式大小电路族的并集，包含 P；它不要求从 $n$ 高效生成该电路。

| 类 | 深度与门 |
|---|---|
| NCⁱ | 深度 $O((\log n)^i)$，布尔门扇入至多 2。 |
| ACⁱ | 相同深度上界；AND/OR 可有无界扇入。 |
| TCⁱ | 再允许无界扇入的多数门。 |

三者均以多项式大小的电路为条件。$\mathsf{NC}^i\subseteq\mathsf{AC}^i\subseteq\mathsf{TC}^i\subseteq\mathsf{NC}^{i+1}$，但不应据此把不同的固定深度类等同。

[精度界与层级](../results/1-upper-bounds.md) · [布尔电路模拟](../results/2-circuit-simulation.md) · [定义原文](../../../TeX/Chain-of-Thought/arXiv-2402.12875v4/preliminary.tex)
