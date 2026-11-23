> [论文索引](../INDEX.MD) · DeepSeek-R1-Zero / Group Relative Policy Optimization

# Group Relative Policy Optimization（GRPO）

对每个问题 $q$，从旧策略 $\pi_{\theta_{\mathrm{old}}}$ 采样 $G$ 个回答 $o_i$，得到奖励 $r_i$。同一题组内归一化以估计优势，不另训价值模型：

$$
A_i=\frac{r_i-\operatorname{mean}(r_1,\ldots,r_G)}{\operatorname{std}(r_1,\ldots,r_G)}.
$$

令 $\rho_i=\pi_\theta(o_i\mid q)/\pi_{\theta_{\mathrm{old}}}(o_i\mid q)$，正文给出的目标写为：

$$
\mathcal J_{\rm GRPO}=\mathbb E_{q\sim P(Q),\,\{o_i\}_{i=1}^G\sim\pi_{\theta_{\mathrm{old}}}(\cdot\mid q)}\left[\frac{1}{G}\sum_{i=1}^{G}\left(\min\left(\rho_i A_i,\operatorname{clip}(\rho_i,1-\epsilon,1+\epsilon)A_i\right)-\beta\widehat D_{\rm KL}\right)\right].
$$

每个输出的 KL 估计项为 $u_i-\log u_i-1$，其中 $u_i=\pi_{\rm ref}(o_i\mid q)/\pi_\theta(o_i\mid q)$。KL 用参考策略，而重要性比率用采样旧策略。

R1-Zero 学习率为 $3\times10^{-6}$，KL 系数 0.001，采样温度 1。每题 16 个输出，每步 32 个不同问题（批量 512）；每 400 步刷新参考模型。每轮 rollout 8,192 个输出，随机划为 16 个 mini-batch，训练 1 个内循环 epoch。最大长度前 8,200 步为 32,768 token，之后为 65,536；总计 10,400 步、约 1.6 epoch。长度上限改变与性能和长度曲线的跳升同期，不能把跳升只归因于模型行为变化。

[PPO 对照](../appendix/1-background.md) · [基础设施](../figures/supp-rl-infrastructure.md) · [Zero 训练曲线](../figures/figure-1-zero-training.md)
