> ⬅️ 返回 [论文索引](../INDEX.MD) · Appendix: Methodological Details

# Dataset examples and feature steering

## Dataset examples

Examples include the most strongly activating excerpts and random excerpts sampled from activation buckets linearly spaced between zero and the maximum. The appendix identifies the Pile (without Books3) and Common Crawl as sources of display examples, rather than the internal training dataset. The display data omit the Human/Assistant chat format. Image examples are curated, mainly from Wikimedia Commons, not drawn at random. With the top-example display, the main text shows representative excerpts from the top 20 and uses token coloring (white for zero, orange for strongest).

## Steering

At a given token, write the activation as $\mathbf{x}=\operatorname{SAE}(\mathbf{x})+\mathbf{e}$, with $\mathbf{e}$ the reconstruction error. Replace one feature coefficient in the reconstruction by a fixed value, add the **unchanged** error back, and run the remaining layers. If a direction $\mathbf{d}_i$ is unit-normalized and $a_i$ is its natural activation, clamping to $c$ changes the residual stream by $(c-a_i)\mathbf{d}_i$. The paper clamps at all token positions in these generation comparisons. Negative clamps are possible even though the encoder itself is nonnegative. Magnitudes are reported in units of the maximum observed activation in the SAE training dataset. Large shifts are interventions, not observations of natural activation. Extremely large clamps (e.g. $\pm100\times$) tend to produce degenerate output.

## Few-shot probe comparison

For seven examples in which SAE steering already worked and a suitable feature could be found from one or two positive examples, the authors formed a comparison vector from the difference of mean middle-layer activations at the final token of positive and negative examples. Few-shot vectors gave similar results in two examples; SAE steering worked where the few-shot comparison did not in the other five. The cases were selected for SAE success and the scale was tuned qualitatively, so this comparison is not an estimate of overall relative performance.

See [behavioral examples](../results/3-behavior.md), [computational intermediates](../results/9-computational-intermediates.md), and [limitations](../discussion/limitations.md).
