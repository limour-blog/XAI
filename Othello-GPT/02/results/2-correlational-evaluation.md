返回 [论文索引](../INDEX.MD) · 结果

# 3.2. Correlational Evaluation

**Lexical sentiment.** Bin first-layer GPT2-small OpenWebText token projections into 20 equal-width buckets, sampling 20 tokens from each. GPT-4 labels them positive, neutral, or negative from the token and a centered 20-token context, with a cursory human sanity check. Negative labels dominate one tail, positive labels the other, and neutral labels the middle. The authors interpret this as consistent with superposition. The top/bottom 0.1% bins distinguish positive and negative tokens with accuracies of 78–89% depending on method; consult the exact values in the [table](../tables/table-figure-3-classification-accuracy.md) and the distribution in [Figure 3](../figures/figure-3-openwebtext.md).

**Negation.** Using GPT2-small's first-layer $K$-means direction, “fail,” “doubt,” and “uncertain” project negatively early and positively later when negated. In the 27-example dataset the change is measured between layers 1 and 10, with direction-dependent sign-flip rates and sizes in the [table](../tables/table-figure-5-negation-experiment.md) and [Figure 5](../figures/figure-5-negation-experiment.md). These observations motivate further analysis of the MLPs; see [negation visualizations](../appendix/a1-4-negations.md) and [neurons](../appendix/a5-neurons.md).
