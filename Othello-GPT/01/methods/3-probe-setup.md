返回 [论文索引](../INDEX.MD) · 方法

# 3. Exploring Internal Representations with Probes

A probe is a classifier or regressor trained on a network's internal activations. The Othello probes use $x_t^l$, summarizing the partial sequence $y_{\leqslant t}$ at layer $l$, and predict a three-way categorical distribution $p_\theta(x_t^l)$ for a tile: black, white, or empty. Occupied versus unoccupied alone is linearly computable from the input sequence, so the authors use the harder three-way target. The current board can be computed from the rules, but it is in general a nonlinear function of the input tokens.

Activation/ground-truth state pairs are split randomly 8:2 for training and validation; the paper reports held-out error. The Section 3 text gives 52.95% for always predicting empty, whereas its Section 3.1 footnote gives 47% for a constant empty prediction. Both figures are retained as stated in the source.

See [linear probe results](../results/2-linear-probes.md) and [nonlinear probe results](../results/3-nonlinear-probes.md).
