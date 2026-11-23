> ⬅️ 返回 [论文索引](../INDEX.MD) · Appendix: Ablations and Attributions

# How well does attribution approximate ablation?

For the “John” emotional inference and the first “Kobe” prompt in the [computational intermediates section](9-computational-intermediates.md), the authors compare the activation of each active feature, its local attribution to a next-token logit contrast, and the change in that contrast under feature ablation. Attribution and ablation correlate at approximately **0.81**; raw activation and ablation correlate at **0.12**. The comparison supports using attribution to shortlist candidates for causal testing in these cases. Attribution is a local approximation; nonlinearities such as saturation in attention can change a finite ablation's effect.

See [Figure 044](../figures/figure-044.md).
