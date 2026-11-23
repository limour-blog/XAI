返回 [论文索引](../INDEX.MD) · 结果

# 4.1. Circuit Analyses

**GPT2-small, ToyMovieReview.** Nine attention heads implement a mixture of direct reading and summarization: identify valenced words at `ADJ` and `VRB`, write a summary at the last `movie` token (`SUM`), and read from `ADJ`, `VRB`, and `SUM` to predict at `END`. Patching the full identified circuit at `ADJ`/`VRB` only along the sentiment direction yields 58.3% logit flips and a 54.8% logit-difference drop; all-direction patching at the same positions yields 97% flips and a 75% drop. This comparison quantifies how much of the circuit's effect is captured by one direction.

**Pythia-2.8B, ToyMoodStories.** The smallest tested model that could perform this task strongly attends to the comma after the queried subject's preference phrase; other words in that phrase are secondary. Heads write to the repeated name and `feels`, and later heads read these to affect `END`. Path patching shows that the comma has a causal role, in addition to behavior visible in raw and value-weighted attention. Value-weighted attention scales the pattern by the norm of the value vector at each position.

See [Figure 7](../figures/figure-7-gpt2-circuit.md), [Figure 8](../figures/figure-8-comma-attention.md), [Figure A.9](../figures/figure-a-9-comma-path-patching.md), and the [detailed circuits](../appendix/a3-detailed-circuits.md).
