← [论文索引](../INDEX.MD)

# Appendix · Score Distributions and Evaluator Validation

## Distribution of scores

What is the distribution of heads<sup>’</sup> scores on our head activation evaluators?

The distribution is sharper in our small models than our full-size models. In both cases, heads with a positive prefix matching score are more likely to have a positive copying score, and this correlation is even stronger for the highes prefix matching scores.

(For models with more than 100 heads, a subset of heads is plotted, as seen in the opaque versus translucent datapoints immediately above.)

![](../images/a97be6394f1db71c3fb000d4bc8bc631254d86227751969ef10d57f008091a8f.jpg)

![](../images/aaa5a9e27c572cddd04180a8cc425ea770a583e5545749053c2a3d9e690b0ccf.jpg)

## Validating head activation evaluators

We show here that our head activation evaluators (that we use to measure the properties in our definition of induction heads) correlate well with mathematically-based measures in small attention-only models.

## Copying

Our copying evaluator correlates well with the OV matrix of each head. Specifically here we plot against the sum of the eigenvalues, divided by the absolute value of the eigenvalues, which is a measure of what fraction of the eigenvalues are positive vs. negative.

![](../images/a19a17a7a28a0724e5f3d1a3d5a94ef6d489b92f6c713868ecd8d95f844953f3.jpg)  
Prefix matching

Our prefix matching evaluator correlates well with the trace of QK eigenvalues for the previous-token QK-circuit term.  
![](../images/135e66395aa084e5b1f909d1f131692bc519c87b0c6ad09dd57d2a6437eefa6e.jpg)

