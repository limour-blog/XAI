返回 [论文索引](../INDEX.MD) · 方法

# Algorithm 1. Attribution via Intervention on Othello-GPT

**Inputs:** Board $B$ and a legal next move $p$ to attribute. **Output:** a sensitivity $S_s$ for each tile $s$.

1. Set $p_0\gets f_p(x_{t-1})$, the unmodified probability of $p$.
2. For each $s\in B$:
   - Set $\tilde{x}_{t-1}\gets\operatorname{Intervention}(x_{t-1},s)$, applying the [single-tile activation edit](4-intervention.md).
   - Set $p_s\gets f_p(\tilde{x}_{t-1})$.
   - Set $S_s\gets p_0-p_s$.

See [the attribution results](../results/5-latent-saliency.md) and [Figure 4](../figures/figure-4-latent-saliency.md).
