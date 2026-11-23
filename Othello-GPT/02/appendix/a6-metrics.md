返回 [论文索引](../INDEX.MD) · 附录

# A.6. Detailed description of metrics

- **Logit difference:** for positive and negative completion sets of $n$ tokens each, $\frac1n\sum_i[\operatorname{logit}(t_i^{\text{positive}})-\operatorname{logit}(t_i^{\text{negative}})]$. A normalized change between the original/counterfactual baselines is used for patching. The continuous measure captures small but important shifts even if the argmax does not change.
- **Logit flip:** proportion of interventions that reverse the sign of the logit difference.
- **Accuracy:** percentage of prompts where the logits for correct answers exceed those for incorrect answers. Usually the two sets are singletons, e.g. `Positive` and `Negative`.

See [interventions](../methods/3-causal-interventions.md) and [causal evaluation](../results/3-causal-evaluation.md).
