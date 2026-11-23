← [论文索引](../INDEX.MD)

# Argument 2 · Architecture intervention

## Argument 2: When we change the transformer architecture in a way that shifts when induction heads form or whether they can form, the dramatic improvement in in-context learning shifts in a precisely matching way.

STRENGTH OF ARGUMENT FOR SUB-CLAIMS

[查看论据 2 的证据强度表](../tables/table-4-architecture.md)

One thing that falls short about Argument 1 is that we<sup>’</sup>re just observing induction heads and incontext learning co-vary; like any observational study, it is not as convincing as if we actively changed one thing and measured what happened to the other. In this section we do a more “interventional” experiment, in which we change the model architecture in a way that makes induction heads easier to form, and observe the effect on in-context learning. The change makes a bigger difference for smaller models so is more convincing there, but also carries some amount of weight for larger models (see table above).

To design our experiment, we start with the observation (noted in the previous section) that the phase change and the corresponding improvement in in-context learning only occurs in transformers with more than one layer. This is what we'd predict if induction heads were the mechanism for the majority of in-context learning: induction heads require a composition of attention heads, which is only possible with two or more layers.<sup>15</sup>

Of course, the observation about one-layer models is pretty weak evidence by itself. (One could imagine one-layer models being different from models with more layers in all sorts of ways!) But it suggests a more general line of attack. If induction heads are the mechanism behind the large improvement in in-context learning, that makes predictions about the minimum architectural requirements in order to achieve the observed improvement. For a standard transformer, the important thing is to have two attention layers. But that's only because the key vectors need to be a function of the attended token and the token before it.

We define a “smeared key" architecture with a very simple modification that should make it easy for transformers of any depth to express induction heads. In our modified models, for each head $h ,$ we introduce a trainable real parameter $\alpha ^ { h }$ which we use as $\sigma ( \alpha ^ { h } ) \in [ 0 , 1 ]$ to interpolate between the key for the current token and previous token $^ { 1 6 }$ :

$$
k _ {j} ^ {h} = \sigma (\alpha^ {h}) k _ {j} ^ {h} + (1 - \sigma (\alpha^ {h})) k _ {j - 1} ^ {h}
$$

The hypothesis that induction heads are the primary mechanism of in-context learning predicts that the phase change will happen in one-layer models with this change, and perhaps might happen earlier in models with more layers. If they're one of several major contributing factors, we might expect some of the in-context learning improvement to happen early, and the rest at the same time as the original phase change.

ONE LAYER

The results (figure below) are in line with the predictions: when we use the smeared-key architecture, in-context learning does indeed form for one-layer models (when it didn<sup>’</sup>t before), and it forms earlier for two-layer and larger models. More such results can be seen in the model analysis table.

[查看 Smeared-key 架构对照图](../figures/figure-9-smeared-key.md)
These plots are an excerpt of the Model Analysis Table; look there to see more analysis of how the smear models compare to their vanilla counterparts.

However, we probably shouldn't make too strong an inference about large models on this evidence. This experiment suggests that induction heads are the <sub>m</sub>i<sub>n</sub>i<sub>ma</sub>l <sub>mec</sub>h<sub>an</sub>i<sub>sm</sub> for greatly increased incontext learning in transformers. But one could easily imagine that in larger models, this mechanism isn<sup>’</sup>t the whole story, and also this experiment doesn<sup>’</sup>t refute the idea of the mechanism of incontext learning changing over the course of training.

