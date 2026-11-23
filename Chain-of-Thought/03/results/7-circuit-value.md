> [返回论文索引](../INDEX.MD) · §4、附录 A

# 电路求值问题（CVP）

随机生成按拓扑顺序排列的 $m$ 门电路，输入中每门用类型、两个输入门编号、当前门编号四个 token 表示。预测最后一门的值；中间标签用类型、两个输入值、当前门值编码。CVP 在 AC⁰ 归约下对 P 完全。实验中 CoT 较 Hint / Base 的优势在低深度尤其明显。

区别：表达能力构造可为给定输入长度的电路家族准备位置嵌入；CVP 的实验则把待求值的随机电路编码为输入，不能把实验设置与证明的输入编码混同。

[图 6](../figures/figure-6-circuit-value.md) · [图 8：Base](../figures/figure-8-serial-base.md) · [实验设置](../methods/3-experimental-setup.md)
