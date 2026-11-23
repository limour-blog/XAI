> [返回论文索引](../INDEX.MD) · §3.1

# Layer-norm hash：消去注意力的分母

严格因果均匀注意力在位置 $i$ 顶多把计数 $x$ 表示为 $x/i$；不同位置分母不同，直接对键与查询做内积不等价于比较计数。作者定义

$$\phi(x,y)=\operatorname{LN}(x,y,-x,-y),\qquad \phi_x=\phi(x,1).$$

用论文的单位范数定义，四维向量均值是零，正比例缩放不改变归一化结果；对 $i>0$，$\phi(x/i,1/i)=\phi_x$。柯西–施瓦茨不等式和第二坐标为正给出 $\phi_q\cdot\phi_k=1$ 当且仅当 $q=k$。于是饱和注意力可对所有匹配的值取平均，或在唯一匹配时选中一个值。

需要读出最新写入时，还要加入足够小的排序项，使它只打破同地址的并列，不让不匹配位置胜过匹配位置。

[自动机](../results/2-automata.md) · [图灵机](../results/3-turing-machines.md) · [附录证明](../appendix/1-proof-guide.md)
