> [返回论文索引](../INDEX.MD) · §4、附录 A

# 模加法：可并行化的对照

输入为独立采样的 $x_i\in\{0,\ldots,p-1\}$ 加终止符 `=`。标签为 $\sum_i x_i\bmod p$，中间结果是前缀模和。$C_7$ 为正文示例，$C_2$ 为奇偶性的附录示例。对数精度模型中，平均/求和与模运算可并行处理，因此在合理长度上浅层 Hint 就有效；CoT 对较长序列改善更明显。有限长度的 float16 实验不与常数精度 AC⁰ 的渐近限制矛盾。

[图 4：C₇](../figures/figure-4-modular-addition.md) · [图 7：C₂](../figures/figure-7-parity.md) · [图 9：Base](../figures/figure-9-modular-base.md)
