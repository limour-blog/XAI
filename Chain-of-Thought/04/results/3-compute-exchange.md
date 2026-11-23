> [返回论文索引](../INDEX.MD) · §7

# 推理计算与预训练计算的换算

用参数数 $N$、预训练 token 数 $D_{\mathrm{pre}}$、推理 token 数 $D_{\mathrm{inf}}$，近似 $X=6ND_{\mathrm{pre}}$、$Y=2ND_{\mathrm{inf}}$。若固定训练数据量、将参数数乘 $M$，大模型总 FLOPs 为 $M(X+Y)$。改用小模型并把差额加到推理，推理预算允许倍率 $M+3(M-1)/R$，其中 $R=D_{\mathrm{inf}}/D_{\mathrm{pre}}$。

比较约大 14 倍参数模型的贪心 pass@1，试验取 $R=0.16,0.79,22$。较易或中等桶、或低推理负载，常能用小模型加测试时搜索/修订超过大模型。困难桶 4/5 或高推理负载下，额外预训练通常更有效。相同总 FLOPs 并不说明延迟相同，也不涉及同时扩展预训练数据和参数的最优配置。

[图 9](../figures/figure-9-flops.md) · [讨论](../discussion/discussion.md)
