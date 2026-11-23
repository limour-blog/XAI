返回 [论文索引](../INDEX.MD) · 结果

# 3.1. Visualizing and Comparing the Directions

Project a token's residual stream at a given layer onto the fitted direction to get its sentiment activation. The five methods yield directions with high cosine similarities. They are not sparse in the residual stream's standard basis. Results are broadly similar across direction estimates, consistent with noisy estimates of one direction.

Neuroscope-style visualization encodes negative scores in red and positive scores in blue. A two-means direction fitted without labels to a set of 30 positive and 30 negative English adjectives yields interpretable extremes in diverse contexts, including French text. This is qualitative and is tested more systematically with correlation and intervention.

See [Figure 1](../figures/figure-1-sentiment-across-texts.md), [Figure 2](../figures/figure-2-direction-similarities.md), [clustering](../appendix/a1-1-clustering.md), and [multilingual examples](../appendix/a1-3-multilingual.md). The authors share [GPT2-small directions](https://github.com/curt-tigges/eliciting-latent-sentiment/tree/main/data/gpt2-small).
