← [论文索引](../INDEX.MD)

# Argument 3 · Direct ablation

## Argument 3: When we directly “knock out” induction heads in small models at test-time, the amount of in-context learning greatly decreases.

STRENGTH OF ARGUMENT FOR SUB-CLAIMS

[查看论据 3 的证据强度表](../tables/table-5-ablation.md)

For the cases they cover, ablations are by far our strongest evidence. The basic argument is that knocking out induction heads decreases the amount of in-context learning we observe in our models. By “knocking out” we mean that we remove a given attention head from the model at test time, doing a forward pass on the transformer without it. (See our methods section for exact details of how the ablation is done.)

The ablations presented below show how attention heads contribute to in-context learning, but we can also do ablations to study how attention heads contribute to the overall behavior change that occurs during the phase change (see the Model Analysis Table).

[查看归纳头消融图](../figures/figure-10-ablation.md)
These plots are a small excerpt of the Model Analysis Table; look there to see the full evidence. See our methods section for exact details of how the ablation is done.

In fact, <sub>a</sub>l<sub>mos</sub>t <sub>a</sub>ll the in-context learning in small attention-only models appears to come from these induction heads! This begins at the start of the phase change, and remains true through the end of training.<sup>17</sup>

Unfortunately, we do not have ablations for our full-scale models. For the models where we do<sup>18</sup> have ablations, it seems like this evidence is clearly dispositive that induction heads increase incontext learning (at least as we've chosen to evaluate it). But can we further infer that they're the primary mechanism? A couple considerations:

In attention-only models, in-context learning must essentially be a sum of contributions from different attention heads. But in models with MLPs, in-context learning could also come<sup>19</sup> from interactions between MLP and attention layers. While ablating attention heads would affect such mechanisms, the relationship between the effect of the ablation on in-context learning and its true importance becomes more complicated. As a result, we can't be fully<sup>20</sup> confident that head ablations in MLP models give us the full picture.

Our ablations measure the marginal effects of removing attention heads from the model. To the extent two heads do something similar and the layer norm before the logits rescales things, the importance of individual heads may be masked.

All things considered, we feel comfortable concluding from this that induction heads are the primary mechanism for in-context learning in small attention-only models, but see this evidence as only suggestive for the MLP case.

