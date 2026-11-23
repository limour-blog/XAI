> ⬅️ 返回 [论文索引](../INDEX.MD) · §7.3 Limitations, Challenges, and Open Problems

# Limitations and open problems

1. **Distribution:** SAE training used text-only activations drawn from a distribution like parts of pretraining, with no images or Human/Assistant-formatted dialogue. Qualitative transfer examples are not coverage estimates for deployment.
2. **Evaluation:** Reconstruction plus L1 is a proxy, not a gold-standard measure of feature quality, model fidelity or interpretability. The trade-off between sparsity and error is not established.
3. **Cross-layer superposition:** A feature can be computed partly in multiple layers. A middle-layer residual stream may capture contributions already accumulated but misses contributions still to be made later.
4. **Completeness and compute:** Even at the studied layer the number of missing features is unknown. A brute-force expansion to all layers may exceed the compute cost of training the language model. The authors suggest exploring more compute- and data-efficient SAE algorithms.
5. **Shrinkage:** An L1 activation penalty systematically reduces nonzero estimates. Reducing reconstruction and sparsity metrics does not automatically produce more interpretable features.
6. **Circuit analysis:** Attention and weight superposition may obstruct reading off interactions even with a feature dictionary. Attribution and ablation provide evidence about specific prompts, not a model-wide circuit map.
7. **Scale of analysis and theory:** The number of features and interactions makes manual interpretation difficult. Automated scoring may help, but higher-dimensional or other nonlinear alternatives to simple feature directions remain plausible.

Related: [discussion of generalization](discussion.md), [dictionary size](../results/7-completeness.md), and [attribution validation](../results/12-ablation-and-attribution.md).
