← [论文索引](../INDEX.MD)

# Argument 1 · Phase change

## Argument 1: Transformer language models undergo a “phase change” during training, during which induction heads form and simultaneously in-context learning improves dramatically.

Our first line of evidence comes from correlating measures of in-context learning and measures of induction head presence over the course of training. Specifically, we observe a tight co-variation between them across dozens of models, of different sizes, trained on different datasets (See Model Analysis Table for more on the models in which we observe this co-occurrence.).

The table below summarizes the quality of this evidence for the models we have studied: it applies to both large and small models, and is the expected outcome if induction heads were responsible for the majority of in-context learning, but it is only correlational and so could be confounded (discussed more below).

STRENGTH OF ARGUMENT FOR SUB-CLAIMS

[查看论据 1 的证据强度表](../tables/table-2-co-occurrence.md)

Our first observation is that if we measure in-context learning for transformer models over the course of training (defined as the 50th token loss minus the 500th token loss as described in Key Concepts), it develops abruptly in a narrow window early in training (roughly 2.5 to 5 billion tokens) and then is constant for the rest of training (see figure below). Before this window there is less than 0.15 nats of in-context learning, after it there is roughly 0.4 nats, an amount that remains constant for the rest of training and is also constant across many different model sizes (except for the one layer model where not much in-context learning ever forms). This seems surprising – naively, one might expect in-context learning to improve gradually over training, and improve with larger mode sizes, as most things in machine learning do.<sup>9</sup>

MODELS WITH MORE THAN ONE LAYER HAVE AN ABRUPT IMPROVEMENT IN IN-CONTEXT LEARNING

ONE LAYER(ATTENTION-ONLY)

[查看上下文学习指标在相变期间的跃迁](../figures/figure-3-phase-change.md)
we highlight theth period of training in plots to make visual comparision between plots easier. The highlighted region is selected for each model based on the derivative of in-context learning.  
Although we only show three models above, the pattern holds true very generally: many examples are shown in the Model Analysis Table later in the paper, including models of varying mode architecture and size.

One might wonder if the sudden increase is somehow an artifact of the choice to define in-context learning in terms of the difference between the 500th and 50th tokens. We'll discuss this in more depth later. But for now, an easy way to see that this is a robust phenomena is to look at the derivative of loss with respect to the logarithm token index in context. You can think of this as measuring something like "in-context learning per ε% increase in context length." We can visualize this on a 2D plot, where one axis is the amount of training that has elapsed, the other is the token index being predicted. Before the phase change, loss largely stops improving around token 50, but after the phase change, loss continues to improve past that point.

## DERIVATIVE OF LOSS WITH RESPECT TO LOG TOKEN INDEX

The rate at which loss decreases with increasing token index can be thought of as something like "in-context learning per token". This appears to be most naturally measured with respect to the log number of tokens

[查看损失对位置的导数](../figures/figure-4-loss-by-position.md)

It turns out that a sudden improvement in in-context learning isn't the only thing that changes in this window. If we go through the attention heads of a model and and score them for whether they are induction heads (using a <sub>pre</sub>fi<sub>x ma</sub>t<sub>c</sub>hi<sub>ng score</sub> which measures their ability to perform the task we used to define induction heads in Key Concepts), we find that induction heads form abruptly during exactly the same window where in-context learning develops (figure below). Again we show only a few models here, but a full set is shown in the Model Analysis Table. The exception is the one-layer model, where induction heads never form – just as in-context learning never substantially develops for the one-layer model.

## INDUCTION HEADS FORM IN PHASE CHANGE

Each line is an attention head, scored by the "prefix matching" evaluation introduced below.

[查看前缀匹配分数](../figures/figure-5-prefix-matching.md)

This already strongly suggests some connection between induction heads and in-context learning, but beyond just that, it appears this window is a pivotal point for the training process in general: whatever's occurring is visible as a bump on the training curve (figure below). It is in fact the only place in training where the loss is not convex (monotonically decreasing in slope).

That might not sound significant, but the loss curve is averaging over many thousands of tokens. Many behaviors people find interesting in language models, such as the emergence of arithmetic, would be microscopic on the loss curve. For something to be visible at that scale suggests it's a widespread, major change in model behavior. This shift also appears to be the first point where, at least for small models, the loss curve diverges from a one-layer model – which does not display the bump, just as it does not display the other abrupt changes.

[查看训练损失与曲线分离的图组](../figures/figure-6-training-loss.md)


We can also apply principal components analysis (PCA) to the per-token losses, as described in per-token-loss analysis, which allows us to summarize the main dimensions of variation in how several models' predictions vary over the course of training.

Below we show the first two principal components of these models<sup>’</sup> predictions, with the golden outline highlighting the same interval shown above, when in-context learning abruptly improved. We see that the training trajectories pivot during exactly the same window where the other changes happen. In some sense, whatever is occurring when in-context learning improves is the primary deviation from the basic trajectory our transformers follow during the course of their training. Once again the only exception is the one-layer model – where induction heads cannot form and incontext learning does not improve.

## PER-TOKEN LOSS PRINCIPAL COMPONENT ANALYSIS

This method is described above, but roughly shows models' training trajectories on the two dimensions there is the most behavioral variance. Note how it abruptly pivots for models with more than one layer.

In summary, the following things all co-occur during the same abrupt window:

Capacity for in-context learning sharply improves (as measured via the in-context learning score).

Induction heads form.

Loss undergoes a small “bump” (that is, the loss curve undergoes a period of visibly steeper improvement than the parts of the curve before and after).

The model<sup>’</sup>s trajectory abruptly changes (in the space of per-token losses, as visualized with PCA).

Collectively these results suggest that some important transition is happening during the 2.5e9 to 5e9 token window early in training (for large models this is maybe 1-2% of the way through training). We call this transition “the phase change”, in that it<sup>’</sup>s an abrupt change that alters the model<sup>’</sup>s behavior and has both macroscopic (loss and in-context learning curves) and microscopic (induction heads) manifestations, perhaps analogous to e.g. ice melting.<sup>10</sup>

## Looking at the Phase Change More Closely

A natural explanation would be that for all these models, the induction heads i<sub>mp</sub>l<sub>emen</sub>t in-context learning: their formation is what drives all the other changes observed. To strengthen this hypothesis a bit, we check a few things. First, the window where the phase change happens doesn<sup>’</sup>t appear to correspond to a scheduled change in learning rate, warmup, or weight decay; there is not some known exogenous factor precipitating everything. Second, we tried out training some of the small models on a different dataset, and we observed the phase change develop in the same way (see Model Analysis Table for more details).<sup>11</sup>

Third, to strengthen the connection a little more, we look qualitatively and anecdotally at what<sup>’</sup>s going on with the model<sup>’</sup>s behavior during the phase change. One way to do this is to look at specific tokens the model gets better and worse at predicting. The model's loss is an average of billions of log-likelihood losses for individual tokens. By pulling them apart, we can get a sense for what's changed.

Concretely, let's pick a piece of text – for fun, we'll use the first paragraph of Harry Potter – and look at the differences in log-likelihoods comparing the start and the end of the phase change. We'll<sup>12</sup> notice that the majority of the changes occur when tokens are repeated multiple times in the text. If a sequence of tokens occurs multiple times, the model is better at predicting the sequence the second time it shows up. On the other hand, if a token is followed by a different token than it previously was, the post-phase-change model is worse at predicting it:

PCA PLOT OF PER-TOKEN LOSSES  
[查看逐 token 损失的训练轨迹 PCA](../figures/figure-7-loss-pca.md)
The training trajectory of models abruptly pivots during a "phase change." We look at the difference and loss before and after. As seen on the right, the change seems to be related to whether text is repeated. The qualitiative change is similar across all models.

## BPER-TOKEN LOSSES ON HARRY POTTER

Mr and Mrs Dursley, of number four, Privet Drive, were proud to say that they were perfectly normal. thank vou very much. They were the last people you'd expect to be involved in anything strange or mysterious, because they just didn't hold with such nonsense. Mr Dursley was the director of a firm called Grunnings, which made drills. He was a big, beefy man with hardly any neck, although he did have a very large moustache. Mrs Dursleywas thin and blonde and had nearly twice the usual amount of neck, which came in very useful as she spent so much of her time craning over garden fences. spving on the neighbours. The Dursleyshad a small son called Dudley and in their opinion there was no finer boy anywhere. The Dursleys had everything they wanted, but they also had a secret, and their greatest fear was that somebody would discover it. They didn't think they could bear it if anyone found out about the Potters. MrsPotter was Mrs Dursley's sister, but they hadn't met for several years; in fact, Mrs Dursley pretended she didn't have a sister, because her sister and her good- for-nothing husband were as unDursleyish as it was possible to be.TheDursleys shuddered to think what the neighbours would say if the Potters arrived in the street. The Dursleysknew that the Potters had a small son, too, but they had never even seen him.This boy was another good reason for keeping the Potters away; they didn't want Dudleymixing with a child like that.

[查看相同与不同后继的例子](../tables/table-3-token-examples.md)

When text is repeated, the post phase-change model better predicts tokens:

... while cases where the same token is followed by a different token are given lower probability

We can also do this same analysis over the course of model training. The loss curve is the average of millions of per-token loss curves. We can break this apart and look at the loss curves for individual tokens.

In particular, let<sup>’</sup>s take a look at per-token loss trajectories for two tokens in the first paragraph of Harry Potter. In red, we show a token whose prediction gets dramatically b<sub>e</sub>tt<sub>er</sub> during the phase change: it<sup>’</sup>s the last of four tokens in “ The Dursleys”, a sequence that appears several times in the text. In blue, we show a token that gets meaningfully <sub>worse</sub> during the phase change: it<sup>’</sup>s the firstever appearance of “ Mrs Potter”, after both previous instances of “ Mrs” were followed by “ Dursley” instead.

[查看两个示例 token 的损失轨迹](../figures/figure-8-token-examples.md)

## PER-TOKEN LOSSES OVER TRAINING

We look at two specific tokens in the Harry Potter passage a to highlight their movement during the phase change.

MrsPotter: This token's loss increases during the phase change, because the model incorrectly predicts that the next token should be "D" from "Dursley".

The Dursleys: This token's loss decreases during the phase change, because the model correctly predicts "leys" based on a previous example.

All of this shows that during the phase change, we see exactly the behaviors we<sup>’</sup>d expect to see if induction heads were indeed contributing the majority of in-context learning.

## Assessing the Evidence

Despite all of the co-occurrence evidence above (and more in the Model Analysis Table), the fact remains that we haven<sup>’</sup>t shown that induction heads are the primary mechanism for in-context learning. We have merely shown that induction heads form at the same time as in-context learning, and that in-context learning does not improve thereafter. There are a number of potential confounds in this story. Below we summarize reasons in favor and against thinking the connection is causal. The argument in favor might look like this:

The formation of induction heads is correlated with a great increase in models' capacity for in-context learning, for a wide variety of models large and small.

It's highly improbable these two sharp transitions would co-occur across so many models by pure chance, without any causal connection.

There is almost surely some connection, and the simplest possibility is that induction heads are the primary mechanism driving the observed increase in in-context learning. (However, as discussed below, it could also be a confounding variable.)

Since over 75% of final in-context learning forms in this window, one might naively believe this to be the amount of in-context learning that induction heads are responsible for.

However, the following issues and confounds suggest caution:

In large models, we have low time resolution on our analysis over training. Co-occurrence when one only has 15 points in time is less surprising and weaker evidence.

Perhaps other mechanisms form in our models at this point, that contribute to not only induction heads, but also other sources of in-context learning. (For example, perhaps the phase change is really the point at which the model learns how to compose layers through the residual stream, enabling both induction heads and potentially many other mechanisms that also require composition of multiple heads) Put another way, perhaps the co-occurrence is primarily caused by a shared latent variable, rather than direct causality from induction heads to the full observed change in in-context learning.

The fact that in-context learning score is roughly constant (at 0.4 nats) after the phase change doesn't necessarily mean that the underlying mechanisms of in-context learning are constant after that point. In particular, the metric we use measures a <sub>re</sub>l<sub>a</sub>ti<sub>ve</sub> loss between the token index 500 and 50, and we know that the model<sup>’</sup>s performance at token 50 improves over training time. Reducing the loss a fixed amount from a lower baseline is likely harder, and so may be driven by additional mechanisms as training time goes on.<sup>13</sup> <sup>14</sup>

One point worth noting here is that the argument that induction heads account for most in-context learning <sub>a</sub>t th<sub>e</sub> t<sub>rans</sub>iti<sub>on po</sub>i<sub>n</sub>t of the phase change is more solid than the argument that they account for most in-context learning <sub>a</sub>t th<sub>e en</sub>d <sub>o</sub>f t<sub>ra</sub>i<sub>n</sub>i<sub>ng</sub> – a lot could be changing during training even as the in-context learning score remains constant.

