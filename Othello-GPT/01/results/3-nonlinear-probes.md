返回 [论文索引](../INDEX.MD) · 结果

# 3.2. Nonlinear Probes Have Lower Error Rates

The nonlinear probe is a two-layer MLP, $p_\theta(x_t^l)=\operatorname{softmax}(W_1\operatorname{ReLU}(W_2x_t^l))$. The paper gives $W_1\in\mathbb{R}^{H\times3}$ and $W_2\in\mathbb{R}^{F\times H}$, with $H$ hidden units. The randomized network sees little improvement with the nonlinear probe. On trained models, nonlinear probe error drops to 1.7% at layer 7 for synthetic training and 9.4% at layer 4 for championship training. These results are consistent with the presence of nontrivial board-state information; decoding alone does not show causal use.

See [Table 2](../tables/table-2-nonlinear-probe-errors.md), [Table 5](../tables/table-5-nonlinear-standard-deviations.md), [Appendix B](../appendix/b-probe-capacity.md), and [causal evaluation](4-causal-role.md).
