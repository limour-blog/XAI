> ⬅️ 返回 [论文索引](../INDEX.MD) · §2.3 Features vs. Neurons

# SAE features versus individual neurons

An SAE fitted to the residual stream may rediscover the output of a single upstream neuron, so the authors compare random 1M SAE features against individual neurons in earlier layers. For **82%** of the sampled features, the highest Pearson correlation with an upstream neuron is **0.3 or less**. The best-matching neurons usually do not share the apparent meaning on visual inspection. The authors also find no strong alignment with individual residual-stream basis coordinates.

Manual inspection compares 50 neurons and 50 features. A separate automated test compares 100 randomly selected units of each type and uses Claude 3 Opus to generate explanations and predict held-out activations. The sampled features score higher on average than MLP neurons; an additional description-to-context rating finds that SAE feature activations are more specific than those of randomly sampled neurons. These measures answer a population-level comparison and do not certify all SAE features as monosemantic.

- [Figure 021 — automated interpretability](../figures/figure-021.md)
- [Figure 022 — specificity](../figures/figure-022.md)
