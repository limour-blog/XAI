> ⬅️ 返回 [论文索引](../INDEX.MD) · Discussion

# Discussion

## To What Extent Does Superposition Exist in Real Models?

Why are we interested in toy models? We believe they are useful proxies for studying the superposition we suspect might exist in real neural networks. But how can we know if they're actually a useful toy model? Our best validation is whether their predictions are consistent with empirical observations regarding polysemanticity. To the best of our knowledge they are. In particular:

Polysemantic neurons exist. Polysemantic neurons form in our third model, just as they are observed in a wide range of neural networks.

Neurons are sometimes "cleanly interpretable" and sometimes "polysemantic", often in the same layer. Our third model exhibits both polyemantic and non-polysemantic neurons, often at the same time. This is analogous to how real neural networks often have a mixture of polysemantic and non-polysemantic neurons in the same layer.

InceptionV1 has more polysemantic neurons in later layers. Empirically, the fraction of neurons which are polysemantic in InceptionV1 increases with depth. One natural explanation is that as features become higher-level the stimuli they detect become rarer and thus sparser (for example, in vision, a high-level floppy ear feature is less common than a low-level Gabor filter's edge). A major prediction of our model is that superposition and polysemanticity increase as sparsity increases.

Early Transformer MLP neurons are extremely polysemantic. Our experience is that neurons in the first MLP layer in Transformer language models are often extremely polysemantic. If the goal of the first MLP layer is to distinguish between different interpretations of the same token (eg. "die" in English vs German vs Dutch vs Afrikans), such features would be very sparse and our toy model would predict lots of polysemanticity.

This doesn't mean that everything about our toy model reflects real neural networks. Our intuition is that some of the phenomena we observe (superposition, monosemantic vs polysemantic neurons, perhaps the relationship to adversarial examples) are likely to generalize, while other phenomena (especially the geometry and learning dynamics results) are much more uncertain.

## Open Questions

This paper has shown that the superposition hypothesis is true in certain toy models. But if anything, we're left with many more questions about it than we had at the start. In this final section, we review some of the questions which strike us as most important: what do we know, and would we like for future work to clarify?

Is there a statistical test for catching superposition?

How can we control whether superposition and polysemanticity occur? Put another way, can we change the phase diagram such that features don't fall into the superposition regime? Pragmatically, this seems like the most important question. L1 regularization of activations, adversarial training, and changing the activation function all seem promising.

Are there any models of superposition which have a closed-form solution? Saxe et al. demonstrate that it's possible to create nice closed-form solutions for linear neural[26] networks. We made some progress towards this for the ReLU output modeln = 2; m = 1 (and Tom McGrath makes further progress in his comment), but it would be nice to solve this more generally.

How realistic are these toy models? To what extent do they capture the important properties of real models with respect to superposition? How can we tell?

Can we estimate the feature importance curve or feature sparsity curve of real models? If one takes our toy models seriously, the most important properties for understanding the problem are the feature importance and sparsity curves. Is there a way we can estimate them for real models? (Likely, this would involve training models of varying sizes or amounts of regularization, observing the loss and neuron sparsities, and trying to infer something.)

Should we expect superposition to go away if we just scale enough? What assumptions about the feature importance curve and sparsity would need to be true for that to be the case? Alternatively, should we expect superposition to remain a constant fraction of represented features, or even to increase as we scale?

Are we measuring the maximally principled things? For example, what is the most principled definition of superposition / polysemanticity?

How important are polysemantic neurons? If X% of the model is interpretable neurons and 1-X% are polysemantic, how much should we believe we understand from understanding the x% interpretable neurons? (See also the "feature packing principle" suggested above.)

How many features should we expect to be stored in superposition? This was briefly discussed in the previous section. It seems like results from compressed sensing should be able to give us useful upper-bounds, but it would be nice to have a clearer understanding – and perhaps tighter bounds!

Does the apparent phase change we observe in features/neurons have any connection to phase changes in compressed sensing?

How does superposition relate to non-robust features? An interesting paper by Gabriel Goh (archive.org backup) explores features in a linear model in terms of the principal components of the data. It focuses on a trade off between "usefulness" and "robustness" in the principal component features, but it seems like one could also relate it to the interpretability of features. How much would this perspective change if one believed the superposition hypothesis – could it be that the useful, non-robust features are an artifact of superposition?

To what extent can neural networks "do useful computation" on features in superposition? Is the absolute value problem representative of computation in superposition generally, or idiosyncratic? What class of computation is amenable to being performed in superposition? Does it require a sparse structure to the computation?

How does superposition change if features are not independent? Can superposition pack features more efficiently if they are anti-correlated?

Can models effectively use nonlinear representations? We suspect models will tend not to use them, but further experimentation could provide good evidence. See the appendix on nonlinear compression. For example investigating the representations used by autoencoders with multi-layer encoders and decoders with really small bottlenecks on random uncorrelated data.

