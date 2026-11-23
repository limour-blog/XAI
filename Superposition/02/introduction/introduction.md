> ⬅️ 返回 [论文索引](../INDEX.MD) · Introduction and key results

# Scaling dictionary learning beyond small transformers

Previous work, [Towards Monosemanticity](https://transformer-circuits.pub/2023/monosemantic-features/index.html), recovered interpretable features from a small one-layer transformer. This study asks whether a similar unsupervised decomposition remains practical for a production language model and whether the resulting units relate to its behavior. It studies the fine-tuned Claude 3 Sonnet, not just the base pretrained model.

The first question is answered by scaling [sparse autoencoders](../methods/1-sparse-autoencoders.md) to three dictionary sizes and analyzing their training loss. Then the authors inspect examples of activation and intervene on the model. Candidate features range from specific entities and places to abstract concepts and code patterns. Some generalize across languages and from text to relevant images even though the SAE training inputs are text-only. The authors also ask whether rare concepts require larger dictionaries, whether features can serve as computational intermediates, and how to find features relevant to safety research.

These are distinct claims: a feature can respond to a concept; editing it can affect a response; neither alone establishes coverage of an entire mechanism or reliable control of a behavior.

See [Figure 002](../figures/figure-002.md), [training results](../results/1-scaling-laws.md), and [feature specificity and influence](../results/2-specificity.md).
