返回 [论文索引](../INDEX.MD) · 结果

# 3.3. Causal Evaluation

**Directional patching.** Fit directions on adjectives and test with unseen adjectives and with verbs that were not used in fitting. Unsupervised $K$-means still moves the logit difference; DAS can flip predictions. [Figure 4](../figures/figure-4-direction-patching.md) reports the best layers for ToyMovieReview and SST. For transfer from the toy data to SST, the strongest effects tend to arise in intermediate layers, rather than the first or last layers ([Figure 6](../figures/figure-6-intermediate-layers.md)). The authors hypothesize that these layers carry a more abstract feature than the embedding alone.

**Activation addition.** In GPT2-small, add a scaled sentiment direction to first-layer residual activations during each forward pass. Starting with “I really enjoyed the movie, in fact I loved it. I thought the movie was just very...”, increasingly negative coefficients produce increasingly negative completions without erasing coherence. See [Appendix A.1.2](../appendix/a1-2-activation-addition.md) and [Figure A.3](../figures/figure-a-3-activation-addition.md).

**SST validation.** Collapse labels to positive/negative, deduplicate test phrases, and exclude the 17% of examples Pythia-1.4B did not classify correctly zero-shot. Pair equal-token-length phrases, yielding 460 clean/corrupted pairs. Prompt with `Review Text: TEXT, Review Sentiment:` and compare `Positive` versus `Negative`. Patching along the toy-trained DAS direction at a single layer flips **53.5%** of outputs in this filtered set. This differs from the [comma ablations](6-sst-summarization.md) on Pythia-2.8B.
