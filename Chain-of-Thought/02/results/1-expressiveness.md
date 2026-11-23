> [返回论文索引](../INDEX.MD) · §1.1

# 解码步数与复杂度类

$$\mathsf{TIME}(t(n))\subseteq\mathsf{CoT}(t(n))\subseteq\mathsf{SPACE}(t(n)+\log n),\qquad
\mathsf{CoT}(t(n))\subseteq\widetilde{\mathsf{TIME}}(n^2+t(n)^2).$$

左侧需要论文指定的严格因果饱和注意力和 projected pre-norm；右侧不依赖这些构造条件。$\widetilde{\mathsf{TIME}}$ 忽略多对数因子。

| 解码预算 | 表达能力 |
|---|---|
| 不生成中间 token | 已知 uniform TC⁰ 上界。 |
| $O(\log n)$ | 在 L 内；未找到一定获益的问题。若 L≠NL，则仍不能识别 NL 完全的有向可达性。 |
| $\Theta(n)$ | 指定架构能识别所有正则语言；上界为线性空间和软二次时间，因此在上下文相关语言内。 |
| $O(n^2)$ | 足以模拟能在二次时间内完成的图可达性算法；未证明二次步是必要的。 |
| 多项式步数的并集 | 指定架构恰好覆盖 P。固定次数的多项式预算不是这个并集。 |

[图 1](../figures/figure-1-hierarchy.md) · [自动机下界](2-automata.md) · [图灵机下界](3-turing-machines.md) · [上界](4-upper-bounds.md)
