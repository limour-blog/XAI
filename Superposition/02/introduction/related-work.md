> ⬅️ 返回 [论文索引](../INDEX.MD) · §8 Related Work

# Related work

- **Theory of superposition:** Near-orthogonal directions, frames and compressed sensing allow an overcomplete description. The authors connect early word-embedding work (Arora et al., Goh) and prior polysemantic-neuron studies to the explicit experiments in [Toy Models of Superposition](../../01/INDEX.MD). Work by Scherlis et al., Henighan et al. and Vaintrob et al. extends the picture to capacity, memorization or computation.
- **Dictionary learning:** Classic sparse coding by Olshausen and Field underlies SAE methods. Yun et al. studied dictionary learning in transformers; Bricken et al. and Cunningham et al. reported interpretable overcomplete features, and Tamkin et al. explored binary codebooks. Later work studied shrinkage, different objectives, attention outputs, other domains and the unexplained residual.
- **Disentanglement:** Disentanglement also seeks isolated factors of variation, but often presupposes no more factors than coordinates. The overcomplete problem studied here is closer to compressed sensing.
- **Feature circuits:** Othello-GPT and language-model work investigate how extracted features interact, beyond identifying them in isolation.
- **Activation steering:** Earlier work perturbs internal activations using statistics from labeled contrasts, hand-specified concepts or learned directions. Sonnet’s SAE dictionary is learned without defining target labels in advance. This paper uses steering as evidence of causal influence, not as a benchmark intended to maximize intervention performance.
- **Safety-relevant measurements:** Linear probes, embedding arithmetic, and contrastive methods have also been used to study bias, truthfulness, confidence and world-state representations. Dictionary learning is one complementary approach.

See [references](../references/references.md).
