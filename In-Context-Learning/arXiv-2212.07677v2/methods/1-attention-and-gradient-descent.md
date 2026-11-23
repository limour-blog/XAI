← [论文索引](../INDEX.MD)

# 2. 线性自注意力可以模拟线性回归的梯度下降

## 自注意力

令 $v_{h,i}=W_{h,V}e_i$、$k_{h,i}=W_{h,K}e_i$、$q_{h,j}=W_{h,Q}e_j$，并将值与键按列堆叠为 $V_h,K_h$。省略偏置，带残差的普通注意力更新为 $e_j\leftarrow e_j+\sum_h P_hV_h\operatorname{softmax}(K_h^\top q_{h,j})$。去掉 softmax 得到线性自注意力（LSA）：

$$
e_j \leftarrow e_j + \sum_h P_h V_h K_h^\top q_{h,j}.
$$

## 将权重更新重写成目标更新

参考模型为 $y(x)=Wx$，上下文样本为 $D=\{(x_i,y_i)\}_{i=1}^N$。原文的损失与 GD 步为

$$
L(W)=\frac1{2N}\sum_{i=1}^N\|Wx_i-y_i\|^2,\qquad
\Delta W=-\frac\eta N\sum_{i=1}^N(Wx_i-y_i)x_i^\top.
$$

令 $\Delta y_i=\Delta W x_i$，则 $L(W+\Delta W)=\frac1{2N}\sum_i\|Wx_i-(y_i-\Delta y_i)\|^2$。因此更新 $W$ 的效果可以通过把每个训练目标替换为 $y_i-\Delta W x_i$ 实现。

## 命题 1：单头线性注意力的显式构造

上下文 token 为 $e_j=(x_j,y_j)$。取

$$
W_K=W_Q=\begin{pmatrix}I_x&0\\0&0\end{pmatrix},\qquad
W_V=\begin{pmatrix}0&0\\W_0&-I_y\end{pmatrix},\qquad
P=\frac\eta N I.
$$

此时 $k_i^\top q_j=x_i^\top x_j$，值的下半块是残差 $W_0x_i-y_i$。代回注意力求和得

$$
P\sum_{i=1}^N v_i(k_i^\top q_j)=(0,-\Delta W x_j),\qquad
e_j\leftarrow(x_j,y_j-\Delta W x_j).
$$

查询用 $(x_{\text{test}},-W_0x_{\text{test}})$ 初始化，取更新后下半块的负值得到 $(W_0+\Delta W)x_{\text{test}}$。键和值只取上下文样本，不让查询影响训练梯度。在单步且 $W_0=0$ 的构造里，查询的值投影为零，可以不排除。多层重复把每一步的变化累加在查询上，并用上一步的残差目标继续更新。

构造并不唯一：单头映射只依赖 $W_{PV}=PW_V$ 和 $W_{KQ}=W_K^\top W_Q$；对两个乘积施加相反的非零标量缩放不改变函数。外循环可跨任务学到合适的有效学习率；输入依赖的曲率统计则可由每个上下文在前向传播中计算。

对应原文 §2 与附录 §A.1（命题 1 的证明）。下一步：[单层结果](../results/1-single-layer.md)、[多层曲率校正](../appendix/10-curvature.md)。
