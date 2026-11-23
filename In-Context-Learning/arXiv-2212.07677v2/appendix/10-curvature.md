← [论文索引](../INDEX.MD)

# A.10 GD++ 曲率校正的构造与谱分析

在命题 1 的键和查询投影不变时，改用

$$
W_V=\begin{pmatrix}I_x&0\\ W&-I_y\end{pmatrix},\qquad
P=\begin{pmatrix}-\gamma I_x&0\\0&(\eta/N)I_y\end{pmatrix}.
$$

对所有 token 的残差更新为 $(-\gamma XX^\top x_j,-\Delta W x_j)$。这保留 GD 的目标残差更新，同时把输入改为 $x_j'=(I-\gamma XX^\top)x_j$。对于以 $H=XX^\top$ 表示的未归一化 Hessian，变换后为 $(I-\gamma H)H(I-\gamma H)^\top$，相应特征值映射为 $f(\lambda)=\lambda(1-\gamma\lambda)^2$。选对 $\gamma$ 可以压小较大的特征值、降低条件数；特征值靠近 $1/\gamma$ 时反而可能失稳。

作者在各 10,000 个任务上改变上下文数据点数量 $N=10,25,50,100$，从训练好的两步循环模型中提取 $\gamma=0.179,0.099,0.056,0.029$。对于 $N=25$，$\gamma=0.099$ 时条件数分布向 1 移动，超过 0.1 后迅速恶化。该分析解释了测试中的加速趋势，而不是任意输入上的最优性证明。

[图 13：谱和条件数](../figures/figure-13-curvature.md) · [多层结果](../results/2-multiple-layers.md)
