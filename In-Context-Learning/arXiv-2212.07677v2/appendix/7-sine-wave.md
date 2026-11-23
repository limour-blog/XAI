← [论文索引](../INDEX.MD)

# A.7 正弦波回归的实验设置

每任务取振幅 $a\sim U(0.1,5)$、相位 $\rho\sim U(0,\pi)$，抽取 $N=10$ 个 $x\sim U(-5,5)$，令 $y=a\sin(\rho+x)$。将 $(x_i,y_i)$ 无偏置投影到 40 维，再用一个带残差的单隐层 MLP（160 个隐单元，GELU）。最后一维作变换后的目标，其余维度作输入特征。查询的目标槽置零。两种方法用相同种子初始化 MLP 和嵌入：一个训练注意力层，另一个固定为 GD 构造并通过更新步骤反传以元学习特征。

[图 4](../figures/figure-4-sine-regression.md) · [正文结果](../results/3-nonlinear-regression.md)
