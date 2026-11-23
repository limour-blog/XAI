> ⬅️ 返回 [论文索引](../INDEX.MD) · §1.2–1.3 SAE experiments and scaling laws

# Training sparse autoencoders on Claude 3 Sonnet

The study uses the fine-tuned Claude 3.0 Sonnet in production at the time of the study, released March 4, 2024. The [SAEs](../methods/1-sparse-autoencoders.md) are trained on **middle-layer residual stream** activations. The residual stream is smaller than the MLP layer and may aggregate features computed across earlier layers. The model's dimensions and some plot units are not reported; the token displays use a simplified tokenizer.

| Run | Dictionary width | Dead features (approx.) |
| --- | ---: | ---: |
| 1M | 1,048,576 | 2% |
| 4M | 4,194,304 | 35% |
| 34M | 33,554,432 | 65% |

In every run, fewer than **300** features were active per token on average; reconstruction explained at least **65%** of activation variance. An SAE feature was counted as dead if it did not activate on a sample of $10^7$ tokens. The L1 coefficient was **5** with the normalization used in the paper.

## Compute allocation

At fixed input dimension and batch setup, compute scales with dictionary width times training steps. The authors train for one epoch, so steps are proportional to data used. Sweeps over width and steps trace the best training loss at each compute budget. Over the tested range, the compute-optimal loss falls roughly as a power law. Both the optimal width and step count grow approximately as power laws; width increases somewhat faster within that range. The authors subsequently sweep learning rates at these recommended settings and extrapolate the decline in compute-optimal learning rate to choose the range for the larger runs. The 34M run's step count follows the compute-allocation analysis.

Training loss is the proxy being optimized; it is not an independently validated measure of interpretability or faithfulness. See [limitations](../discussion/limitations.md).

- [Figure 003 — compute and loss](../figures/figure-003.md)
- [Figure 004 — training steps versus dictionary width](../figures/figure-004.md)
