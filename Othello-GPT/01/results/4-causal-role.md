返回 [论文索引](../INDEX.MD) · 结果

# 4.2. Evidence for a Causal Role for the Representation

A benchmark example gives the model a partial game, a tile, and a target state. One subset of 1,000 examples consists of natural (legally reachable) positions; a second subset of 1,000 consists of unnatural positions unreachable in legal play. These unnatural states are a stricter test because they are outside the training distribution.

For each case, let $N$ be the number of legal moves on the counterfactual board. Compare the model's top $N$ moves with this set; the score is the number of false positives plus false negatives. The null baseline scores the unchanged predictions against the same post-intervention legal move set.

| Benchmark | Null intervention | Best intervention |
|---|---:|---:|
| Natural | 2.68 | 0.12 |
| Unnatural | 2.59 | 0.06 |

The main text reports $L_s=4$ (five layers edited) for both best results. The effect at even unreachable positions supports a causal role for the representation in next-move prediction. See [Figure 3](../figures/figure-3-intervention-errors.md), the [intervention protocol](../methods/4-intervention.md), [counterfactual heatmaps](../appendix/c-counterfactual-heatmaps.md), and [alternative metrics](../appendix/f-alternative-metrics.md).
