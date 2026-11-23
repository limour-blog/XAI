← [论文索引](../INDEX.MD)

# A.8 梯度下降、核最小二乘与核平滑

考虑只变换输入的残差 MLP：$(x_j,y_j)\mapsto(m(x_j),y_j)$，其中 $m(x)=x+\tilde m(x)$。由命题 1，LSA 对该 token 的 $y$ 槽写入 $-\Delta Wm(x_j)$。从 $W_0=0$ 开始，一步更新的查询预测相当于用 $m(x_i)^\top m(x_{\text{test}})$ 对上下文标签加权求和；按正文损失和步长定义，整体比例为 $\eta/N$。因此单步可作核平滑解释，多步则可看作优化同一个核化平方损失，而不只是重复做固定的加权平均。构造可只在第一块保留 MLP；实践中各层 MLP 如何改变目标或核留待研究。

[正文命题 2](../results/3-nonlinear-regression.md)
