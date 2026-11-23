返回 [论文索引](../INDEX.MD) · 附录

# F. Alternative Metrics for the Intervention Experiment

The legal move set changes by an average set difference of 2.12 tiles. Top-1 legality is nearly saturated for the synthetic model, so the paper reports multi-label $F_1$ as well as the error count. It also measures KL divergence between the predicted move distribution and a discrete uniform distribution over the legal moves. These are averages over 1,000 individual cases rather than a single score on pooled predictions. All three metrics show similar trends as the starting layer changes.

See [Figure 9: F₁](../figures/figure-9-intervention-f1.md), [Figure 10: KL divergence](../figures/figure-10-intervention-kl.md), and the [primary benchmark](../results/4-causal-role.md).
