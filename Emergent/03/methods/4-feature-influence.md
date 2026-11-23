> [返回论文索引](../INDEX.MD) · §3.4 · [图 1](../figures/figure-1-gradient-paths.md)

# 沿训练轨迹估计各梯度分量的影响

用最终模型的探针方向 $w$ 作参照。特征失配是两个参数配置的残差特征投影差的平方的一半：

$$R(x\mid\theta_1,\theta_2,w)=\tfrac12(\langle w,r_{\theta_1,i}^k(x)\rangle-\langle w,r_{\theta_2,i}^k(x)\rangle)^2.$$

影响 $I$ 是目标失配对方向 $G$ 的一阶方向导数，即 $\nabla_\theta R(x\mid\theta,\theta^*,w)^\top G$。在每一步估计三类方向的影响，沿检查点求和以解释从初始到最终的特征变化。原文对 SGD 给出小步长的一阶近似；Adam 情形为每类梯度维护独立一阶矩，使用共同的逐坐标缩放以拆分优化器步。这一归因按实际训练轨迹计算，不是三个独立训练过程的对比。

先训练得到 $\theta^*$ 并拟合探针，再用同种子和数据顺序重跑，以便测得相同轨迹上的各分量。见[附录 B](../appendix/2-attribution.md)。
