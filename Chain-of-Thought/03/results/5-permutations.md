> [返回论文索引](../INDEX.MD) · §4、附录 A

# S₅ 置换复合

从五元集合的置换中独立采样，目标为整个复合置换。若 $\pi$、$\sigma$ 是置换，则 $(\sigma\circ\pi)_i=\sigma_{\pi_i}$。训练的中间标签是每一前缀的复合结果。CoT 能把这些部分置换写回，Hint 只对输入前缀施加监督。图注指出无 CoT 时准确率多数时候约 20%，相当于随机猜其中一个位置的值；不要把这个数当成整个置换联合猜中的概率。

[图 3](../figures/figure-3-permutations.md) · [图 8：Base](../figures/figure-8-serial-base.md) · [理论分离](2-circuit-simulation.md)
