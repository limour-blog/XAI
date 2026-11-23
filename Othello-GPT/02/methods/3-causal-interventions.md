返回 [论文索引](../INDEX.MD) · 方法

# 2.3. Causal Interventions

**Activation patching:** Pair original and sentiment-flipped prompts of the same length and format, e.g. “This movie was great” versus “This movie was terrible.” Capture the original activations, then replace one component's activation at a time in the flipped run. If the replacement restores the original behavior, the component has a causal effect in the experiment.

**Directional activation patching:** Replace only the activation projected onto a unit vector $\mathbf d$ with the projection from the counterpart input. For a recipient $\mathbf o$ and donor $\mathbf o'$, this is $\mathbf o+[(\mathbf o'-\mathbf o)\cdot\mathbf d]\mathbf d$. Equivalently, patch a single coordinate after rotating the basis. Measure the logit difference or the fraction of examples whose predicted sentiment flips.

**Ablation:** Remove a component's contribution by setting output to zero or a dataset mean. For directional ablation remove only the component along a specified direction. **Path patching:** restrict patching to the paths from selected senders to receivers, holding the rest of the upstream network fixed.

See [metrics](../appendix/a6-metrics.md), [causal evaluation](../results/3-causal-evaluation.md), and [SST summarization ablations](../results/6-sst-summarization.md).
