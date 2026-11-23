> [返回论文索引](../INDEX.MD) · §4、附录 A

# 迭代平方

合成任务用 $r$、素数 $p$ 和一串平方记号编码输入，范围 $1\le r,p\le 999$，目标为 $r^{2^n}\bmod p$，$n$ 是平方次数。中间结果是每次平方后的模值。CoT 的每步只需平方并取模；论文报告深度 1 的 CoT 也可表达该实验任务。实验使用的小素数实例不满足引言引用的密码学困难性假设的技术条件，因此不能把此结果当成该假设的验证。

[图 5](../figures/figure-5-iterated-squaring.md) · [图 8：Base](../figures/figure-8-serial-base.md)
