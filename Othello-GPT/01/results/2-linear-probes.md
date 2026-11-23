返回 [论文索引](../INDEX.MD) · 结果

# 3.1. Linear Probes Have High Error Rates

The linear classifier is $p_\theta(x_t^l)=\operatorname{softmax}(Wx_t^l)$, where $W\in\mathbb{R}^{F\times3}$ in the paper's notation and $F$ is the activation dimension. No error dips below 20%; the strongest results are 20.4% on the synthetic model and 23.6% on the championship model, versus 26.7% on the randomly initialized model. The random network still preserves some information about moves, so the important comparison is between the trained and randomized networks rather than against a constant-only guess. In this black/white/empty formulation, the tested linear probes only modestly improve on the randomized model.

See [Table 1](../tables/table-1-linear-probe-errors.md), [Table 4](../tables/table-4-linear-standard-deviations.md), and [nonlinear probes](3-nonlinear-probes.md).
