> ⬅️ 返回 [论文索引](../INDEX.MD) · §2.1 Influence on Behavior

# Model behavior under feature interventions

[Specificity](2-specificity.md) supports an association between a feature and a concept. To test downstream influence, the authors clamp feature activity with the SAE error preserved. A Golden Gate Bridge clamp (`34M/31164353`, **10×** the observed maximum) leads the model to describe itself as the bridge. Clamping the transit infrastructure feature (`1M/3`, **5×**) causes the model to mention a bridge when it otherwise would not. The behaviors are consistent with the interpretations but these manipulations do not establish that natural activations at ordinary magnitudes are necessary for those outputs.

See [Figure 009](../figures/figure-009.md) and [the steering procedure](../methods/2-dataset-and-steering.md).
