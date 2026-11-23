返回 [论文索引](../INDEX.MD) · 方法

# 4–4.1. Validating Probes with Interventional Experiments: Intervention Technique

For a partial game, record the next-move prediction from the original board state $B$. Modify the activations so the probe reports a counterfactual $B'$ that differs from $B$ on a single tile $s$. The set of legal moves changes. If predictions shift to the legal moves of $B'$, this provides evidence that the probed representation affects the output.

Using the probe's class score for the selected tile, optimize the activation $x$ while freezing the model and probe weights. The loss is cross-entropy against the desired state; $\alpha$ is the learning rate:

$$
x' \leftarrow x - \alpha\,\frac{\partial \mathcal{L}_{\mathrm{CE}}(p_\theta(x), B')}{\partial x}.
$$

An $L$-layer model run on $T$ tokens has an $L\times T$ grid of activations. At the last token, successively replace $x^l_{T-1}$ with its edited value from layer $L_s$ through $L$, resuming the forward calculation after each replacement. This counters the possibility that a later layer repairs an isolated edit by using untouched information from earlier positions or layers.

See [Figure 2](../figures/figure-2-intervention-scheme.md), [intervention results](../results/4-causal-role.md), [layer-by-layer probe interaction](../appendix/d-inter-probe-interaction.md), and [hyperparameters](../appendix/g-intervention-hyperparameters.md).
