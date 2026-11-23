← [论文索引](../INDEX.MD) · [模型分析指标](7-model-analysis.md)

# Model Analysis Table · Small attention-only models


This experiment series studies small attention-only transformers. because these are the models we have the strongest theoretical understanding of (see the framework paper). For these small models, we're able to capture snapshots with a high time resolution over early training. These experiments are the ones that most cleanly demonstrate the phase change and link it to induction heads. Note how (1) many models undergo a discontinuous phase change (seen most clearly in the PCA plot and in-context learning score): (2) it appears to be caused by induction heads (see ablations); and (3) the only model without a phase change is the onelayer model. More...

## PCA OF TOKEN LOSSES

![](../images/2363502c3cc35ed9d80c13d1b788fa7b78c4401d15dea5e5f66ff383b83227a9.jpg)

## MODELS OVER TRAINING

## LOSS OVER TRAINING

![](../images/e7aeebb56bd6131a99dc5c9ac56f4c120e75c568abc8713de9b42242b9f47099.jpg)

## LOSS OVER TRAINING, BROKEN DOWN BY CONTEXT INDEX

![](../images/69c56a9dfb5800f7252113281b54593efd71f7ca7f55907bd06644bf4eb08304.jpg)

## DERIVATIVE OF LOSS WRT CONTEXT INDEX

![](../images/e97fc01d7ad3cbc84c001e6ad7eab8c1a6be4f3f874cc0c1f9b4c75105431c36.jpg)

## "IN-CONTEXT LEARNING SCORE"

How much better the model is at predicting the 500th token than the 50th? We use this as a proxy for how good the model is at in-context

![](../images/ac1c92a010c177cf9fe2c7864b325e1d6e38e3214d249bfa0cf30b757dac4fa1.jpg)

## ATTENTION HEADS OVER TRAINING

## "PREFIX MATCHING SCORE"

Each line is an attention head. Y axis is the average fraction of a head's attention weight given to the token we expect an induction head to attend to -- the token where the prefix matches the present context -- on random synthetic data. Heads are colored by layer depth early;late. More...

## TRACE OF QK EIGENVALUES

Each line is an attention head. Y axis is the trace of the W in the attention head's Id $h _ { \mathrm { p r e v } } \otimes W$ QK circuit term, scaled by how well hprey matches an ideal previous token head. Only defined for models more than one layer deep. Heads are colored by laver depth:early:

## ABLATION TO "BEFORE-AND-AFTER" VECTOR

Each line is an attention head. Y axis is the projection of the observed per-token loss differences when ablating an attention head onto the difference in per-token losses before and after the bump. More... Heads are colored by type:

previous token;induction;other.

## ABLATION ATTRIBUTION TO "IN-CONTEXT LEARNING SCORE"

Each line is an attention head. Y axis is the change in the "in-context learning score" observed when ablating each attention head. previous token;induction;other.

![](../images/dc2c534b708ad9d7d5d3913b71b2eead9610d3537ef5698fc88fc94ee1c1f624.jpg)

![](../images/b1544ace57d4dbe2512fe1a5cec2a80175121a7a850a7d7f799edac7876bd443.jpg)

![](../images/a70717b5ed694e62b412a9b496fe3889160c608a9981f306eb4c28aae51e633e.jpg)

![](../images/542977116bd9c58cda475e3020e42af6df4b22f7ab15ecbb073ac984607fe504.jpg)

Loss(ntrain, ictx = 500)

