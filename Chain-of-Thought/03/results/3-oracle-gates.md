> [返回论文索引](../INDEX.MD) · §3.4

# 嵌入宽度与 oracle 门

在多项式嵌入宽度和零指数位下，论文给出双向刻画：$T$ 步 CoT 对应 $O(1+T)$ 个门的电路，其中常数精度可以调用 AC⁰ oracle 门，对数精度可以调用 TC⁰ oracle 门。每个 oracle 门可处理多项式长度输入，大小计门而不是连线。令 $T=0$ 得直接输出模型分别等于 AC⁰ 与 TC⁰。

对固定 $k$，给定 $T(n)=n^k$ 时，多项式宽度可严格强于对数宽度（精度 $s(n)=O(\log n)$，固定点）；直接输出也有宽度分离。然而把预算对所有多项式取并集后，两种宽度都达到 P/poly。

[常数精度图](../figures/figure-1-constant-precision.md) · [对数精度图](../figures/figure-10-log-precision.md) · [证明导读](../appendix/1-proof-and-experiment-guide.md)
