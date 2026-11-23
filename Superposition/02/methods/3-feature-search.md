> ⬅️ 返回 [论文索引](../INDEX.MD) · §5 Searching for Specific Features

# Search strategies for dictionaries with millions of units

1. **Single prompts:** Inspect high activations for an example and a token position likely to contain the desired concept. Generic or token-specific features can compete with the concept feature.
2. **Prompt combinations:** Compare activations over positive prompts and filter with negative examples; this can remove background features common to many prompts. The source notes that negative images helped exclude features common to unrelated images.
3. **Geometry:** Inspect nearby decoder vectors by cosine similarity. This is useful for navigation around a known feature; see [the neighborhood survey](../results/6-neighborhoods.md).
4. **Attribution:** Rank active features by their estimated contribution to a contrast between candidate next-token logits; see [computational intermediates](../results/9-computational-intermediates.md) and [ablation validation](../results/12-ablation-and-attribution.md).

These procedures retrieve candidates, not ground-truth labels. Inspecting randomly sampled and strongly activating examples, testing alternative interpretations, and using causal controls answer separate questions.
