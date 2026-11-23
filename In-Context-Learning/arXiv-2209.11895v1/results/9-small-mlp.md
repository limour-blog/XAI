← [论文索引](../INDEX.MD) · [模型分析指标](7-model-analysis.md)

# Model Analysis Table · Small models with MLPs


This experiment series studies small normal transformers (with MLP layers, unlike the above). For these small models, we're able to capture snapshots with a high time resolution over early training. The main observation to take away is that the results are essentially the same as the attention-only models (where we have a stronger theoretical understanding. More...

ONE LAYER(WITH MLPS)

TWO LAYER (WITH MLPS)

THREE LAYER (WITH MLPS)

FOUR LAYER (WITH MLPS)

FIVE LAYER (WITH MLPS)

SIX LAYER (WITH MLPS)

## PCA OF TOKEN LOSSES

The vector of per-token losses is a way to map different neural network behavior to the same vector space. We take 10,000 individual token predictions per model, and project them onto the first two principal components. This shows how the large-scale-behavior of multiple networks

![](../images/71b9d5a34b723528023946cb94940d742b7b975be173ad9d07a5bda354672f27.jpg)

## MODELS OVER TRAINING

## LOSS OVER TRAINING

The orange banddenotes phase change interval.

## LOSS OVER TRAINING, BROKEN DOWN BY CONTEXT INDEX

Heatmap of Loss(ntrain, ictx), the average loss of ictx token in context after ntrain elapsed

## DERIVATIVE OF LOSS WRT CONTEXT INDEX

Heatmap of dLoss(ntrain, ictx) / d ln(ictx). The log vertical partial derivative of the above graph.

## "IN-CONTEXT LEARNING SCORE"

How much better the model is at predicting the 500th token than the 50th? We use this as a proxy for how good the model is at in-context

![](../images/5f90528956fe24622801d4343050d0d7e96bbcdeb176df59a3baac953dc501ea.jpg)

![](../images/3aee3e8115391539e4922b0223afbcd53093edaf78849508fba13d35fed3c7ce.jpg)

![](../images/d6fa5eb0a3e75459d60e83e9d3644b1a430f103b7dd9b08ead43c325a6723c59.jpg)

![](../images/29d67720fd4f25de69bda72d1e49e4542b5c8de79f9314a4bc41848c531519b8.jpg)

## ATTENTION HEADS OVER TRAINING

## "PREFIX MATCHING SCORE"

Each line is an attention head. Y axis is the average fraction of a head's attention weight given to the token we expect an induction head to attend to -- the token where the prefix matches the present context -- on random synthetic data. Heads are colored by layer depth: early;late. More...

## TRACE OF QK EIGENVALUES

Each line is an attention head. Y axis is the trace of the W in the attention head's Id © hprev © W matches an ideal previous token head. Only defined for models more than one layer deep. Heads are colored by layer depth:early;

## ABLATION TO "BEFORE-AND-AFTER" VECTOR

Each line is an attention head. Y axis is the projection of the observed per-token loss differences when ablating an attention head onto the difference in per-token losses before and after the bump. More... Heads are colored by type:

previous token;induction;other.

## ABLATION ATTRIBUTION TO "IN-CONTEXT LEARNING SCORE"

Each line is an attention head. Y axis is the change in the "in-context learning score" observed when ablating each attention head. More... Heads are colored by type: previous token:induction:other.

![](../images/ae0338033b109d234335d9ca0740844c924010401f303dece8801c2d7d92318e.jpg)

![](../images/bb9f8ca87e7e0f10c8a6638b62f06726d5b89413465263d8c51a71d8b8ead026.jpg)

![](../images/2851765e1dcd5b9a88ce65bd8082f092ae476d21e92d7964819ce86774a51b1e.jpg)

![](../images/662a1e1791f6bd2b42bcd5bad0691680c31ac1d31bf426873340e8e4270e3ec0.jpg)

![](../images/98f2272857a0a88bfbd328179bf6b13e1c475951c0f36717946d04097ddb3ffa.jpg)  
The vector of per-token losses is a way to map different neural network behavior to the same vector space. We take 10,000 individual token predictions per model, and project them onto the first two principal components. This shows how the large-scale-behavior of multiple networks evolve over training. More...

