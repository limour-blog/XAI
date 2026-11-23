返回 [论文索引](../INDEX.MD) · 附录

# A.2. Is sentiment really a hyperplane?

DAS can find more than one direction. In GPT2-small, increasing subspace dimension improves the in-sample patching score on movie-review adjectives but not the out-of-distribution score on a character mood dataset with varying adverbs. In [Figure A.6](../figures/figure-a-6-das-dimensions.md), run index $n$ means dimension $2^{n-1}$; loss is one minus the usual patching metric. See [direction estimation](../methods/2-direction-finding.md).
