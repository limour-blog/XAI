← [论文索引](../INDEX.MD)

# 3. 合成回归任务、训练目标与对齐指标

每个任务 $\tau$ 抽取无噪声线性教师 $W_\tau\sim\mathcal N(0,I)$，独立采样 $x_{\tau,i}\sim U(-1,1)^{n_I}$，令 $y_{\tau,i}=W_\tau x_{\tau,i}$。多数实验使用 $N=n_I=10$、$n_O=1$。将 $N$ 个上下文样本编码为 $(x_i,y_i)$，另加查询 $(x_{\text{test}},0)$，从最终查询 token 的 $y$ 分量读出预测。目标函数只监督查询：

$$
\mathcal L(\theta)=\frac1B\sum_{\tau=1}^B\left\|\hat y_\theta(\{e_{\tau,i}\}_{i=1}^N,e_{\tau,N+1})-y_{\tau,\text{test}}\right\|^2.
$$

外循环使用 Adam；在线训练每个更新步重新采样一批任务。GD 基线从 $W_0=0$ 出发。单层比较中，用 $10^4$ 个训练任务做学习率线搜索，另用 $10^4$ 个验证任务测量预测之差的 L2 范数、预测对 $x_{\text{test}}$ 的导数之差和导数的余弦相似度。在线性设置中，后两项直接比较前向传播所得的有效线性模型。非线性设置中，这些指标只比较局部函数值和一阶项。

为区分“损失相同”和“实现相同”，作者也比较权重乘积的插值、分布外输入/教师缩放，以及把单层重复执行的轨迹。参见[训练超参数](../appendix/12-experimental-details.md)、[权重插值](../appendix/3-weight-interpolation.md)和[分布外比较](../appendix/2-ood.md)。
