← [论文索引](../INDEX.MD) · [模型分析指标](7-model-analysis.md)

# Model Analysis Table · Smeared-key and dataset controls

## "SMEARED KEY" ARCHITECTURE MODIFICATION + CONTROLS

This experiment series analyzes "smeared key" models, which are designed so that a single attention layer can implement induction heads (see Argument 2). For each smeared key model, a regular control model is provided (trained exactly the same) for comparison. The key observations are that (1) a one-layer smeared-key model experiences the phase change, while a regular onelayer model does not; and (2) the two-layer smeared-key model experiences a phase change earlier than a baseline model. More..

ONE LAYER (VANILLA)

ONE LAYER (SMEARED KEYS)

TWO LAYER (VANILLA)

TWO LAYER (SMEARED KEYS)

![](../images/48392fb5b264cf531c4b764fc781edefbe03547fb8b279f2ecd98abf176cc810.jpg)

## LOSS OVER TRAINING, BROKEN DOWN BY CONTEXT INDEX

Heatmap of Loss(ntrain, ictx), the average loss $i _ { \mathrm { c t x } }$ token in context after ntrain elapsed

![](../images/65e969ea445f61e6b48db8d84f972950c3b2c349fed45db929ca21d9c3220208.jpg)

## DERIVATIVE OF LOSS WRT CONTEXT INDEX

Heatmap of dLoss(ntrain, ictx) / d ln(ictx). The log vertical partial derivative of the above graph.

![](../images/7e37039d0f06a8952155ba6c2653863358fc6c8a70151d4ada7bee636a351158.jpg)

## "IN-CONTEXT LEARNING SCORE"

How much better the model is at predicting the 500th token than the 50th? We use this as a proxy for how good the model is at in-context

![](../images/3c5ee55875e71370e38d75d08cb007ed817dbac2f19291b2479c07e9c7f1ecc7.jpg)

## SMALL ATTENTION-ONLY TRANSFORMERS (DIFFERENT DATASET)

This experiment series studies transformers of the same architecture as the small attention-only transformers, on a different dataset consisting only of internet books. More..

ONE LAYER(ATTENTION-ONLY)

![](../images/9de6791e1507b01f4fccc13875eba72e73df52359c785820d27d28f1be620747.jpg)

## SMALL TRANSFORMERS (WITH MLPS) (DIFFERENT DATASET)

This experiment series studies small normal transformers (with MLP layers), on a different dataset consisting only of internet books

![](../images/39639de64083ace05b8e75700a1eec4ff7eb6b9d32e4df61f05bfad11d14c220.jpg)  
How much better the model is at predicting the 500th token than the 50th? We use this as a proxy for how good the model is at in-context

