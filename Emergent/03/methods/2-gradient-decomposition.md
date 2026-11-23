> [返回论文索引](../INDEX.MD) · §3.1 · [图 1](../figures/figure-1-gradient-paths.md)

# 按残差流路径分解损失梯度

取位置 $i$ 和层 $k$，令 $L_i$ 是预测 $x_{i+1}$ 的损失，$L_j^{\mathrm{sg}(k,i)}$ 是在该残差流应用 stop-gradient 后的形式（前向不变）。

$$\begin{aligned}
G_{\mathrm{direct}}&=\nabla_\theta(L_i-L_i^{\mathrm{sg}(k,i)}),\\
G_{\mathrm{pre}}&=\nabla_\theta\sum_{j\ne i}(L_j-L_j^{\mathrm{sg}(k,i)}),\\
G_{\mathrm{shared}}&=\sum_j\nabla_\theta L_j^{\mathrm{sg}(k,i)}.
\end{aligned}$$

- **直接**：经过该残差流且影响下一 token。
- **预缓存**：经过该残差流并经注意力影响更远的 token；因果遮罩排除更早的损失。
- **共享**：不经过该残差流，却能通过共享参数影响产生该激活的计算。

命题 3.1：三项恰好加总为全梯度。见[附录 A](../appendix/1-gradient-proof.md)。
