> ⬅️ 返回 [论文索引](../INDEX.MD) · §7.1–7.2 Discussion

# What the findings mean for safety and generalization

A training corpus can contain descriptions of undesirable behavior, so the existence of a candidate direction for that concept is not itself evidence that the model intends or will carry out the behavior. The relevant questions are when such a feature activates, whether it contributes to the output in the natural regime, and whether measurements transfer beyond the examples used to discover it. Splitting the same concept across several SAE features or grouping distinct mechanisms in one unit can change apparent conclusions. Feature activation patterns and downstream effects can also differ.

Two observations motivate further work: some text-trained features activate on images, and some features respond both to abstract discussions and to concrete instances of a concept. These are examples of transfer, not proof that an interpretability-based safety assessment generalizes to unfamiliar settings. The authors discuss possible uses in monitoring, steering and safety evaluation while noting that there is no basis here for a complete safety guarantee.

See [safety-relevant feature studies](../results/11-safety-relevant-features.md) and [limitations](limitations.md).
