> [返回论文索引](../INDEX.MD) · §3.2

# 有限自动机：线性步识别正则语言

**定理（源标签 `thm:automata`）**：对任何正则语言 $L$，有 projected pre-norm 的饱和注意力解码器可在带起始标记的输入上，用 $|x|+1$ 个解码步判断 $x\in L$。构造可以不用额外位置编码，也可放宽严格因果掩码；需要模型能辨认起始位置。

给定 DFA $(\Sigma,Q,q_0,\delta,F)$，先写初态 $q_0$；生成阶段逐个读回上一状态 $q$，同时用均匀注意力获得当前输入索引的倒数，并通过 [layer-norm hash](../methods/2-layer-norm-hash.md) 匹配原始输入位置。前馈层执行有限转移表 $\delta$，最后检查 $q_n\in F$。每个新状态回填给下一步，相当于显式递归。

若 uniform TC⁰≠NC¹，直接解码模型不能识别所有正则语言，这给出条件分离。[能力总览](1-expressiveness.md) · [层级图](../figures/figure-1-hierarchy.md)
