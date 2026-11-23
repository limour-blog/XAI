返回 [论文索引](../INDEX.MD) · 讨论与结论

# 6. Limitations

- A dominant direction may capture a mixture of more specific sentiment features rather than a universal axis. Positive and negative directions are equivalent to appropriate sums/differences of a valence axis and a sentiment axis: $\mathbf p=\mathbf x+\mathbf y$, $\mathbf n=\mathbf x-\mathbf y$, or $\mathbf x=(\mathbf p+\mathbf n)/2$, $\mathbf y=(\mathbf p-\mathbf n)/2$.
- The causal abstractions do not explain all task performance. Distributed representations, superposition, self-repair, or omitted circuit components may explain the remaining performance. More diverse templates may separate task-specific machinery from sentiment processing.
- Small datasets plus many metrics and hyperparameters create a risk of overfitting. Tests on SST and other models give independent checks. DAS can overfit or induce out-of-distribution activations; simpler methods such as logistic regression provide comparisons.

See [Section 3.3](../results/3-causal-evaluation.md) and [DAS dimensionality](../appendix/a2-das-dimensions.md).
