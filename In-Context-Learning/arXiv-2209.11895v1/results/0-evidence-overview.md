← [论文索引](../INDEX.MD)

# Overview of the evidence

Now we<sup>’</sup>ll proceed to the main part of the paper, which makes the case that induction heads may <sub>prov</sub>id<sub>e</sub> th<sub>e pr</sub>i<sub>mary mec</sub>h<sub>an</sub>i<sub>sm</sub> for the majority of in-context learning for transformer models in general. As stated in the introduction, this is a very broad hypothesis and much of our evidence is indirect, but nevertheless we believe that all the lines of evidence together make a relatively strong, though not conclusive, case.

Before we go through the arguments, it<sup>’</sup>s useful to delineate where the evidence is more conclusive vs. less conclusive. This is shown in the table below. For small, attention-only models, we believe we have strong evidence that attention heads are the mechanism for the majority of in-context learning, as we have evidence supported by ablations and mechanistic reverse engineering. Conversely, for all models, we can make a strong case that induction heads play <sub>some ro</sub>l<sub>e</sub> in incontext learning, as we can demonstrate examples and show suggestive correlations. However, the larger the models get, the harder it is to establish that induction heads account for the actual <sub>ma</sub>j<sub>or</sub>it<sub>y</sub> of in-context learning. For large models with MLP<sup>’</sup>s, we must therefore rely on mainly correlational evidence, which could be confounded. We explore alternate hypotheses throughout, including at the end of Argument 1 and again briefly in Argument 6.

SUMMARY OF EVIDENCE FOR SUB-CLAIMS (STRONGEST ARGUMENT FOR EACH)

[查看证据总表](../tables/table-1-evidence-summary.md)

Here is the list of arguments we<sup>’</sup>ll be making, one per section, repeated from the introduction:

Argument 1 (M<sub>acroscop</sub>i<sub>c</sub> <sub>co</sub>-<sub>occurrence</sub>): Transformer language models undergo a “phase change” early in training, during which induction heads form and simultaneously in-context learning improves dramatically.

Argument 2 (M<sub>acroscop</sub>i<sub>c</sub> <sub>co</sub>-<sub>per</sub>t<sub>ur</sub>b<sub>a</sub>ti<sub>on</sub>): When we change the transformer architecture in a way that shifts whether induction heads can form (and when), the dramatic improvement in in-context learning shifts in a precisely matching way.

Argument 3 (Di<sub>rec</sub>t <sub>a</sub>bl<sub>a</sub>ti<sub>on</sub>): When we directly “knock out” induction heads at test-time in small models, the amount of in-context learning greatly decreases.

Argument 4 (S<sub>pec</sub>ifi<sub>c examp</sub>l<sub>es o</sub>f i<sub>n</sub>d<sub>uc</sub>ti<sub>on</sub> h<sub>ea</sub>d <sub>genera</sub>lit<sub>y</sub>): Although we define induction heads very narrowly in terms of copying literal sequences, we empirically observe that these same heads also appear to implement more sophisticated types of in-context learning, including highly abstract behaviors, making it plausible they explain a large fraction of incontext learning.

Argument 5 (M<sub>ec</sub>h<sub>an</sub>i<sub>s</sub>ti<sub>c p</sub>l<sub>aus</sub>ibilit<sub>y o</sub>f i<sub>n</sub>d<sub>uc</sub>ti<sub>on</sub> h<sub>ea</sub>d <sub>genera</sub>lit<sub>y</sub>): For small models, we can explain mechanistically how induction heads work, and can show they contribute to incontext learning. Furthermore, the actual mechanism of operation suggests natural ways in which it could be repurposed to perform more general in-context learning.

Argument 6 (C<sub>on</sub>ti<sub>nu</sub>it<sub>y</sub> f<sub>rom sma</sub>ll t<sub>o</sub> l<sub>arge mo</sub>d<sub>e</sub>l<sub>s</sub>): In the previous 5 arguments, the case for induction heads explaining in-context learning is stronger for small models than for large ones. However, many behaviors and data related to both induction heads and in-context learning are smoothly continuous from small to large models, suggesting the simplest explanation is that mechanisms are the same.

For each argument, we<sup>’</sup>ll have a similar table to the one in this section, showing the strength of the evidence provided by that claim as it applies to large/small models and some/most of context learning. The table above is the sum of the evidence from all six lines of reasoning.

