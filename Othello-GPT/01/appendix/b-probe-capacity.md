返回 [论文索引](../INDEX.MD) · 附录

# B. Ablation on Nonlinear Probe Accuracies

The authors vary the number of MLP hidden units $H$ and the source layer $l$. More capacity generally improves decoding and intermediate or later-middle layers decode better than the ends. The "what-how-where" analysis replaces training stage in the earlier "what-when-where" plots with probe capacity.

They also bin validation examples by how many steps a tile has been in its current state. With moderately sized nonlinear probes, accuracy shows an inverted-U pattern: concepts are better decoded after they have persisted for some time, but not too long. The paper interprets this as consistent with delayed updating and later forgetting.

See [Figure 6](../figures/figure-6-probe-capacity.md) and [nonlinear probe results](../results/3-nonlinear-probes.md).
