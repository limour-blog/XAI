← [论文索引](../INDEX.MD)

# Model Details


## SMALL MODELS

The small models are 1- through 6-layer Transformers. These include models both with MLPs and without MLPs (i.e. “attention only” models). They have a context window of 8192 tokens, a 216 token vocabulary, an activation dimension dmodel = 768, and 12 attention heads per layer regardless of total model size. They were trained for 10,000 steps (\~10 billion tokens), saving 200 snapshots at intervals of every 50 steps. Their positional embeddings are implemented with a variant on the standard positional embeddings (similar to Press <sub>e</sub>t <sub>a</sub>l. ). The training dataset is[17] described earlier at the start of the Model Analysis Table.

We observe a “phase change” phenomenon that appears at approximately 1-3 billion tokens in the small models. It might be reasonable to ask whether these phenomena are driven by scheduled changes to the hyperparameters, such as learning rate or weight decay. Weight decay was reduced at 4750 steps (approximately 5 billion tokens), the effects of which can be seen as a slight deviation about halfway through the displayed loss curves, occurring at the exact same point for all models; this is not related to the phase change, as this step number is notably beyond the range in which the phase change occurs. The only other hyperparameter change that occurs within the range of the phase change is the learning rate warm-up, which ramps up over the first 1.5e9 tokens.

## FULL-SCALE MODELS

The “full-scale models” are from the same set of models as described in Askell <sub>e</sub>t <sub>a</sub>l. The[18] context window and vocabulary size are the same as the small models (that is, 8192 tokens and 216 tokens respectively). Unlike the small models, their dimensions are adjusted to scale up with increasing size, with an activation dimension $d _ { m o d e l } = 1 2 8 * n _ { l a y e r }$ , and a varying number of attention heads (See Appendix for full details). The models have both dense and local attention heads. In a local attention head, each token may only attend to earlier tokens within a fixed window of relative positions. Dense heads are the standard head, where a token may attend to <sub>any</sub> earlier token (including itself). The training dataset is described earlier at the start of the Model Analysis Table.

Snapshots from these models were saved at exponential step numbers, at an interval of $2 \mathsf { x } .$ For our analyses we use snapshots at steps from $_ { 2 } \wedge _ { 5 }$ through $2 ^ { \wedge } 1 7 ,$ plus one or two final saves thereafter, for a total of 15 saved snapshots (except the 40L which has 14 saved snapshots). This<sup>26</sup> corresponds to a consistent number of tokens across all models up through 2^11 steps $( = 2 . 1 5 \mathsf { E } + 0 9 $ tokens), after which adjustments to the training schedule cause the number of tokens per step to increase for the 24L and 40L models.

## TABLE OF MODEL PROPERTIES FOR FULL-SCALE MODELS

[查看大规模模型规格表](../tables/table-10-model-properties.md)

## SMEARED KEY MODELS

The “smeared $\mathsf { k e y } ^ { \prime \prime }$ architecture modification described in Argument 2 is as follows: we introduce a trainable real parameter used asα $\sigma ( \alpha ) \in [ 0 , 1 ]$ that interpolates between the key for the current token and previous token:

$$
k _ {j} = \sigma (\alpha) k _ {j} + (1 - \sigma (\alpha)) k _ {j - 1}
$$

(In the case of the very first token in the context, no interpolation happens). These models were otherwise proportioned and trained exactly the same as the small models. We present these only at one-layer and two-layer sizes.

