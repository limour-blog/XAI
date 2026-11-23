← [论文索引](../INDEX.MD)

# Appendix · Data Collection


We measure several properties of the model<sup>’</sup>s overall behavior and of each constituent attention head. With the exception of the attention head ablations (which are the most computationally-intensive, and so were run only on the small models), we measure these properties on all snapshots of all models across training (that is, 200 snapshots each for the twelve small models, and 14 or 15 snapshots each for the six full-scale models). By measuring them on each snapshot, we can see how each property evolves over the course of training, rather than simply measuring the fina model.

The properties we collect data on are as follows:

1 . Per-token losses with unaltered models

2. Per-token losses with ablations of individual attention heads

3. Empirical head measurements with head activation evaluators: using heuristics to score attention heads based on their observed activations, as another way of estimating “copying”, “prefix matching” and “previous token” attention.

4. Mathematical head measurements with the trace of QK eigenvalues for the previous-token QK-circuit term: measuring how much the WQWK weight matrix reads in a subspace affected by heads that attend to the previous token.

## (1) Per-token losses (unaltered models)

The most straightforward property we measure is per-token losses from each model snapshot. We run the mode snapshot on a set of 10,000 randomly-selected examples from the dataset, each of which is 512 tokens in length, and save individual token losses for every token. The set is held the same between all snapshots and between all models in al three families.

When analyzing the per-token loss data, we summarize it in two different ways:

Random token per example. For each example, we extract the loss for just one random token out of the 512 tokens and discard the rest, giving a length-10,000 vector for each model snapshot. (The random index used for each example is consistent between each model.)

Context index average. We average the per-token losses by context index (i.e. by position), giving a length-512 vector for each model snapshot. The i<sub>con</sub>t<sub>ex</sub>tth entry in the vector is an average over the 10,000 tokens drawn from position i<sub>con</sub>t<sub>ex</sub>t in each example.

## (2) Per-token losses (attention head ablations)

One way to study individual attention heads is to measure the difference between the complete model<sup>’</sup>s overall behavior and the overall behavior of a model that is exactly the same except for missing that head. We do this by successively ablating (i.e. zeroing-out) each attention head<sup>’</sup>s contribution to the residual stream. The approach of removing a head<sup>’</sup>s contribution can be thought of as loosely similar to a genetic “knockout” experiment in biology, where observing the effect of removing a specific gene can provide information about the gene<sup>’</sup>s function.

We could do these ablations in two different ways: a “full” ablation, and a “pattern-preserving” ablation. (The mode analysis table shows only pattern-preserving ablations; we explain the other method for comparison) The full ablation would remove <sub>a</sub>ll of a head<sup>’</sup>s contributions to model behavior, whereas the pattern-preserving ablation removes the ablated head<sup>’</sup>s contribution to all later heads<sup>’</sup> <sub>ou</sub>t<sub>pu</sub>t <sub>vec</sub>t<sub>ors</sub>, but preserves the ablated head<sup>’</sup>s contribution to all later heads<sup>’</sup> attention tt .<sup>29</sup>

Full ablation

M<sub>e</sub>th<sub>o</sub>d: Run the model, replacing the ablated attention head<sup>’</sup>s result vector with a zero vector.

O<sub>u</sub>t<sub>come</sub>: All downstream computations are impacted (including all Q, K, and V calculations, and attention patterns).

Pattern-preserving ablation (shown in Model Analysis Table)

M<sub>e</sub>th<sub>o</sub>d:

Step 1: Run the model for the first time, saving all attention patterns and discarding the output logits.

Step 2: Run model a second time. Replace the ablated attention head<sup>’</sup>s result vector with a zero vector, and force all attention patterns to be the version recorded in the first run.

O<sub>u</sub>t<sub>come</sub>: Only downstream V calculations are affected by the ablation, not Q and K calculations. The contribution a head makes to later layers<sup>’</sup> attention patterns is preserved.<sup>30</sup>

This is by far the most computationally-intensive measurement we perform, although fortunately it consists of many small single-GPU jobs and so we could often run it in “spare” capacity.

As a quick note of comparison, our previous work in Transformer Circuits also contained ablation experiments. Although there are similarities (most notably the decision to freeze patterns), the specific ablations we describe here are i<sub>n</sub>di<sub>v</sub>id<sub>ua</sub>l <sub>a</sub>tt<sub>en</sub>ti<sub>on</sub> h<sub>ea</sub>d ablations where only one attention head is modified at a time, whereas the ablations described in our prior work are th- d t ablations in which all attention heads are manipulated at once and the process is repeated iteratively <sub>n</sub> times.

## (3) Head activation evaluators

We construct three heuristic measurements of attention heads, to score how strongly a head exhibits specific properties of interest. These are empirical measurements, based on observed activations on example data.

We evaluate heads on the following properties:

Copying. Does the head<sup>’</sup>s direct effect on the residual stream increase the logits of the same token as the one being attended to?

Prefix matching. On repeated sequences of random tokens, does the head attend to earlier tokens that are followed by a token that matches the present token?

Previous token attention. Does the head attend to the token that immediately precedes the present token?

(Note that “copying” is a property that depends on a head<sup>’</sup>s OV circuit, whereas “prefix matching” and “previous token attention” are properties that depend on a head<sup>’</sup>s QK circuit.)

We are interested in these properties in particular — copying, prefix matching, and previous token attention — because they are relevant to induction heads<sup>’</sup> function of predicting repeated sequences of random tokens. Specifically, (1) a head with both a “copying” OV circuit and a “prefix matching” QK circuit is thereby an induction head by our definition, because it attends to previous instances of the present token and increases the logit of the token that followed; and (2) a “previous token” head can be used as an algorithmic component of a future induction head in a later layer (as we explain in more detail in Argument 5).

In more detail, each head evaluator is implemented as follows, and each score is averaged over 10 examples

C<sub>opy</sub>i<sub>ng</sub>: Generate a sequence of 25 random tokens, excluding the most common and the least common tokens. Compute this head<sup>’</sup>s contribution to the residual stream, then convert that using the unembeddings (i.e. along the “direct path”) to impacts on each logit. Logits are transformed by subtracting the mean of the logits and passing through a ReLU, allowing the evaluator to focus on where logits are raised. Compute the ratio of the amount it raises the logits of the token being attended to, to that of all tokens in this sample. This value ranges from 0 (only raises other tokens) to 0.5 (only raises the present token), so we scale it into the range of -1 to 1.

P<sub>re</sub>fi<sub>x ma</sub>t<sub>c</sub>hi<sub>ng</sub>: Generate a sequence of 25 random tokens, excluding the most common and the least common tokens. Repeat this sequence 4 times and prepend a “start of sequence” token. Compute the attention pattern.<sup>31</sup> The prefix matching score is the average of all attention pattern entries attending from a given token back to the tokens that preceded the same token in earlier repeats.

P<sub>rev</sub>i<sub>ous</sub> t<sub>o</sub>k<sub>en</sub>: Draw an example from the training distribution. Compute the attention pattern. The previous token score is the average of the entries of all the attention pattern entries attending from token i to token i-1.

In the Appendix we validate the connection between these empirical measurements and the mathematical properties o attention head weight matrices explored in Transformer Circuits, and show a joint distribution of scores for copying and prefix matching, for heads in the small and large models.

## (4) Trace of QK eigenvalues (for previous-token QK-circuit term)

In addition to the heuristic measurements described above, we construct another measure of prefix matching that draws on concepts from A Mathematical Framework for Transformer Circuits. In short, we measure how overall large and positive the eigenvalues are of the matrix found in the term of the QK circuit that corresponds specifically to “pure K-W composition” with heads that attend to the previous token. Positive eigenvalues of indicate “same-matching”:W preferring that this component of the query and key vectors be the same. A “same-matching” matrix associated withW a “previous token” term in the QK circuit is a simple way to implement basic prefix matching behavior. We unpack here more about what this measure is and how it is computed.

The “QK circuit” is a term we coined in our previous work to refer specifically to the entire transformation $C _ { Q K } ^ { h }$ which is applied to the one-hot token vectors to compute the attention patternt $A ^ { h }$ for a specific head: $A ^ { h }$ = softmax<sup>∗</sup> $\left( t ^ { T } \cdot C _ { Q K } ^ { h } t \right)$ . The full computation of $C _ { Q K } ^ { h }$ for a given head can be decomposed into many terms, each corresponding to one of the many paths through the model that needs to be computed in order to map tokens to their attention scores for that head. The section Path Expansion of Attention Scores QK Circuit in our earlier work shows all the terms of a full expansion for a two-layer model; models with more layers have QK circuits with even more terms.

For this measure, we narrow the scope of our calculation to the simplest possible term of the QK circuit that could contribute to the “prefix-matching” behavior of an induction head: namely, only pure K-composition terms (in which the query-side term is just the direct path from the embeddings), and furthermore only the subset of those that correspond specifically to K-composing with an earlier head that consistently attends to the immediately previous token.

In order to compute this measure for a given head, we do the following:

1 . For all attention heads in earlier layers, measure how “previous-token-like” the head is, as the average of the attention pattern along the previous-token off-diagonal, over an example text.

2. Compute the matrix found in each individualW Id ⊗ $A ^ { h _ { k } } \otimes W _ { E } ^ { T } W _ { Q K } ^ { h } W _ { O V } ^ { h _ { k } } W _ { E }$ term, for each head in earlie layers.

3. Create a combined matrix by weighting the matrices in step 2 by the measurement in step 1 of how “previous-W token-like” each previous head is.

4. Measure the trace (i.e. the sum of the eigenvalues) of this combined weighted matrix.W

Because this measure relies on K-composition with heads in previous layers, it is only defined for models more than one layer deep, and only for attention heads in the second layer and beyond.

We show in the Appendix that this measure correlates well with our heuristic prefix matching evaluator on our small models.

