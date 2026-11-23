← [论文索引](../INDEX.MD)

# Related Work


The general approach of this paper to reverse engineering transformers is based heavily on our previous paper, A M<sub>a</sub>th<sub>ema</sub>ti<sub>ca</sub>l F<sub>ramewor</sub>k f<sub>or</sub> T<sub>rans</sub>f<sub>ormer</sub> Ci<sub>rcu</sub>it<sub>s</sub>. There is much to be said about how that framework relates to other work in interpretability. Rather than repeating it, we refer readers to Related Work in our previous paper, especially discussion of the relationship to circuits , to analysis of attention heads (<sub>e</sub>.<sub>g</sub>. ), and to related mathematical analysis (<sub>e</sub>.<sub>g</sub>.[6] [24, 25, 26, 27, 28] ).[29]

Building on that perspective, we here focus on how aspects of this paper raise new connections to the machine learning literature, separate from the connections raised simply by the underlying framework.

## IN-CONTEXT LEARNING

Emergent in-context learning was compellingly demonstrated in GPT-3 . A number of papers[1] have studied how to effectively leverage in-context learning, especially with "prompt engineering" . But of particular importance to us, several papers have tried to study how and when in-[11, 12] context learning occurs (<sub>e</sub>.<sub>g</sub>. ).[13, 30, 31, 32]

Some of the findings of these papers are consistent with the induction head hypothesis, or support our methodology:

Kaplan <sub>e</sub>t <sub>a</sub>l. is the origin of our approach for using loss at different token indices as a[13] formalism for studying in-context learning.

O<sup>’</sup>Connor & Andreas find that preserving word order in contexts is important, as the[30] induction head hypothesis would suggest.

However, there are also places where experiments in these papers seem in tension with the induction head hypothesis:

O<sup>’</sup>Connor & Andreas have some experiments suggesting that removing all words except[30] nouns can improve loss. This seems inconsistent with the induction head hypothesis. However, they only find this for experiments where they retrain the model on modified data. This seems both less directly related to our work (because we aim to study models trained on natural data) and subtle to interpret (because retraining models introduces the possibility of run-to-run loss variation, and the measured loss differences are small). The experiments where they don't retrain models on modified data seem consistent with the induction head hypothesis.

Xie <sub>e</sub>t <sub>a</sub>l. finds that LSTMs outperform Transformers when fit to synthetic data generated[31] by a Hidden Markov Model (HHM) designed to isolate a particular theoretical model of incontext learning. We generally expect Transformers to outperform LSTMs at in-context learning on natural text (as seen in Kaplan <sub>e</sub>t <sub>a</sub>l. ), with induction heads as a major[13] explanation. But in the case of the Xie <sub>e</sub>t <sub>a</sub>l. experiments (which don<sup>’</sup>t use natural text), we suspect that the structure of the synthetic data doesn't benefit from Transformers, and that LSTMs are perhaps better at simulating HMMs.

Note that we are using a broader conception of “in-context learning”, rather than something as specific as “few-shot learning”. This is in contrast with Brown <sub>e</sub>t <sub>a</sub>l. , which describes that a[1] language model “develops a broad set of skills and pattern recognition abilities. It then uses these abilities at inference time to rapidly adapt to or recognize the desired task,” with examples of tasks such as few-digit addition and typo correction. In our conception of “in-context learning”, we refer to all the ways that a model rapidly adapts to or recognizes what is going on in the context, even if “what is going on in the context” isn<sup>’</sup>t well-conceived-of as multiple “shots” of some other specific repeated task.

## SCALING LAWS

Over the last few years, the observation that machine learning models change in smooth, predictable ways described by scaling laws has emerged as a useful tool for modelling the[13] properties of models before training them.

The relationship between scaling laws and mechanistic interpretability might be seen as analogous to the relationship between thermodynamics and the physics of individual particles. For both thermodynamics and scaling laws, even though the underlying system is very complicated, we're able to find simple relationships between the variables – for thermodynamics: entropy, temperature, volume and pressure; for neural networks: loss, compute, parameters, and data. In contrast, mechanistic interpretability studies the individual circuits underlying our models, vaguely analogous to how one might carefully study individual particles in physics. In physics, these two layers of abstraction were bridged by statistical physics.

Can we bridge these two levels of abstraction in machine learning? The induction head phase change is the first time we're aware of a bridge. They give us a phenomenon at the level of macroscopic properties at loss which can be explained at the level of circuits and mechanistic interpretability.

In fact, induction heads may be able to explain previous observed exceptions to scaling laws. In our work, 1-layer transformers seem very different from deeper transformers. This was previously observed by Kaplan <sub>e</sub>t <sub>a</sub>l. who found that 1-layer transformers do not follow the same scaling[13] laws as larger transformers. It seems quite plausible that the reason why the scaling laws are different for one-layer models is that they don't have induction heads.

## PHASE CHANGES & DISCONTINUOUS MODEL BEHAVIOR

In the previous section, we discussed how scaling laws describe smooth predictable relationships between model loss and properties like scale. However, a more recent set of results have made the situation seem more subtle. While models<sup>’</sup> losses often scale in predictable ways, there are cases where behavior is more complex:

Brown <sub>e</sub>t <sub>a</sub>l. find that, while aggregate loss scales predictably with model size, models[1] ability to perform specific tasks like arithmetic can change abruptly.

Power <sub>e</sub>t <sub>a</sub>l. observe a phenomenon they call "grokking" where models discontinuously[8] jump from random chance to perfect generalization as they train.

Double Descent is a phenomenon where model performance first gets worse due to[33] overfitting as one makes a model larger (the "classical” regime), but then gets better again past a certain point (the "modern" regime). Generalizations of double descent can occur with respect to parameter size, dataset size, or amount of training . These phenomena are not[34] discontinuous in loss, but they are surprising trend reversals, and perhaps discontinuous in derivatives.

For more general discussion of these phase change phenomena, see a recent blog post by Steinhardt [35].

The discontinuous phase change behavior we observe with induction heads is most analogous to Power <sub>e</sub>t <sub>a</sub>l. 's "grokking", in that it occurs over the course of training. We think our main[8] contribution to this literature is linking the changes we observe to the formation of induction heads and a parameter-level understanding of the circuits involved. As far as we know, induction heads are the first case where a mechanistic account has been provided for a phase change in machine learning.

## LEARNING DYNAMICS

If neural networks can genuinely be understood mechanistically, in terms of circuits, it seems like there almost h<sub>as</sub> t<sub>o</sub> be some way to understand the learning process in terms of the dynamics of circuits changing. Induction heads offer an interesting preliminary bridge between these topics, and are a source of optimism for such a connection. This section will briefly review some strands of work on the learning dynamics side, which seem particularly promising to think about if one wanted to pursue such a connection further.

One remarkable result in learning dynamics, by Saxe <sub>e</sub>t <sub>a</sub>l , has been the discovery of <sub>c</sub>l<sub>ose</sub>d[23] f solutions to learning dynamics for linear neural networks without activation functions. The exciting thing about this work is that it actually provides a simple way to conceptually think about neural network learning in a simplified case. (In follow up work, Saxe <sub>e</sub>t <sub>a</sub>l also explore connections between this framework and models learning to represent semantic information .) We're unable[36] to provide a detailed review of this work here, but we note that Saxe <sub>e</sub>t <sub>a</sub>l's framework could naturally suggest a circuit lens for thinking about learning dynamics. Very roughly, they find that linear neural networks can be understood in terms of the evolution of independent paths through the network, with each path corresponding to a principal component of the data. These paths might be thought of as circuits.

Another interesting line of work has been the study of the geometry of neural network loss surfaces (<sub>e</sub>.<sub>g</sub>. ). Here, our thoughts on the connection are more superficial, but it seems like[37, 38, 39, 40] there must be some way in which aspects of the loss surface connect to the formation of circuits. Very concretely, it seems like the phase change we've described in this paper must correspond to some very large feature in the loss landscape of transformers.

## UNIVERSALITY

In the context of interpretability and circuits, "universality" or "convergent learning" is when[41] [42] multiple models develop the same features and circuits. Universality might seem like an intellectual curiosity, but the circuits thread argues that universality plays a critical role in what kind of interpretability makes sense:

[I]<sub>mag</sub>i<sub>ne</sub> th<sub>e s</sub>t<sub>u</sub>d<sub>y o</sub>f <sub>ana</sub>t<sub>omy</sub> i<sub>n a wor</sub>ld <sub>w</sub>h<sub>ere every spec</sub>i<sub>es o</sub>f <sub>an</sub>i<sub>ma</sub>l h<sub>a</sub>d <sub>a comp</sub>l<sub>e</sub>t<sub>e</sub>l<sub>y</sub> <sub>unre</sub>l<sub>a</sub>t<sub>e</sub>d <sub>ana</sub>t<sub>omy</sub>: <sub>wou</sub>ld <sub>we ser</sub>i<sub>ous</sub>l<sub>y s</sub>t<sub>u</sub>d<sub>y any</sub>thi<sub>ng o</sub>th<sub>er</sub> th<sub>an</sub> h<sub>umans an</sub>d <sub>a coup</sub>l<sub>e</sub> d<sub>omes</sub>ti<sub>c an</sub>i<sub>ma</sub>l<sub>s</sub>? I<sub>n</sub> th<sub>e same way</sub>, th<sub>e un</sub>i<sub>versa</sub>lit<sub>y</sub> h<sub>ypo</sub>th<sub>es</sub>i<sub>s</sub> d<sub>e</sub>t<sub>erm</sub>i<sub>nes w</sub>h<sub>a</sub>t f<sub>orm o</sub>f <sub>c</sub>i<sub>rcu</sub>it<sub>s researc</sub>h <sub>ma</sub>k<sub>es sense</sub>. If it <sub>was</sub> t<sub>rue</sub> i<sub>n</sub> th<sub>e s</sub>t<sub>ronges</sub>t <sub>sense</sub>, <sub>one cou</sub>ld i<sub>mag</sub>i<sub>ne a</sub> ki<sub>n</sub>d <sub>o</sub>f “<sub>per</sub>i<sub>o</sub>di<sub>c</sub> t<sub>a</sub>bl<sub>e o</sub>f <sub>v</sub>i<sub>sua</sub>l f<sub>ea</sub>t<sub>ures</sub>” <sub>w</sub>hi<sub>c</sub>h <sub>we o</sub>b<sub>serve an</sub>d <sub>ca</sub>t<sub>a</sub>l<sub>ogue across mo</sub>d<sub>e</sub>l<sub>s</sub>. O<sub>n</sub> th<sub>e</sub> <sub>o</sub>th<sub>er</sub> h<sub>an</sub>d, if it <sub>was mos</sub>tl<sub>y</sub> f<sub>a</sub>l<sub>se</sub>, <sub>we wou</sub>ld <sub>nee</sub>d t<sub>o</sub> f<sub>ocus on a</sub> h<sub>an</sub>df<sub>u</sub>l <sub>o</sub>f <sub>mo</sub>d<sub>e</sub>l<sub>s o</sub>f <sub>par</sub>ti<sub>cu</sub>l<sub>ar</sub> <sub>soc</sub>i<sub>e</sub>t<sub>a</sub>l i<sub>mpor</sub>t<sub>ance</sub> <sub>an</sub>d h<sub>ope</sub> th<sub>ey</sub> <sub>s</sub>t<sub>op</sub> <sub>c</sub>h<sub>ang</sub>i<sub>ng</sub> <sub>every</sub> <sub>year</sub>. [41]

Research on universality began with Li <sub>e</sub>t <sub>a</sub>l. who showed that many neurons are highly[42] correlated with neurons in retrained versions of the same model. More recently, a number of papers have shown that in aggregate, neural networks develop representations with a lot of shared information (<sub>e</sub>.<sub>g</sub>. ). The Circuits thread tried to extend this notion of universality from features[43, 44] to <sub>c</sub>i<sub>rcu</sub>it<sub>s</sub>, finding that not only do at least some families of well-characterized neurons reoccur across multiple networks of different architectures and that the same circuits , but the same[41] circuits appear to implement them .[45]

Certain kinds of universality are often implicitly assumed in the language model attention head interpretability literature. For example, it seems widely accepted that "previous token" attention heads form across many transformer language models (<sub>e</sub>.<sub>g</sub>. ). The implicit hypothesis of[26, 27] universal attention heads – that is, attention heads with the same attention patterns in different models – isn't exactly the same thing as the kind of feature universality studied in the vision context, but is kind of analogous.

Our work in this paper has analogies to many of these strands of prior work. Like the previous attention head papers, we describe the induction head pattern as a universal attention pattern. However, our analysis of these heads<sup>’</sup> OV and QK circuits extends this claim of universality to the circuit level, similar to the original Circuits thread. And a corollary of our analysis of the OV circuit is a claim about what feature the attention head computes (roughly: the token embedding of the token following a previous copy of the present token) which is more similar to the traditional work on universality.

Separate from all of this, it's worth mentioning that increasingly there's evidence for a particularly extreme kind of universality at the intersection of neuroscience and deep learning. Increasingly, research suggests that biological and artificial neural networks learn similar representations (<sub>e</sub>.<sub>g</sub>. ). In fact, Goh <sub>e</sub>t <sub>a</sub>l. find that multimodal "concept" neurons found in humans (such as[46, 47, 48] [49] the famous "Jennifer Anniston neuron") occur in neural networks.

## ATTENTION PATTERNS IN TRANSLATION-LIKE TASKS

In Argument 4, we saw an induction head that helps implement translation. Although we're not aware of anything quite so general in the prior literature, there are reports of attention patterns which, in retrospect, seem somewhat similar. Often, in translation-like tasks, we see attention attend to the token which is <sub>a</sub>b<sub>ou</sub>t t<sub>o</sub> b<sub>e</sub> t<sub>rans</sub>l<sub>a</sub>t<sub>e</sub>d. We see this in literal translation (<sub>e</sub>.<sub>g</sub>. ) and[50] also in voice recognition (<sub>e</sub>.<sub>g</sub>. where the model attends to the portion of the audio about to be[51] transcribed). Visualizations of this in the encoder-decoder context often slightly obscure the induction-like nature of the attention patterns, because the decoder is visualized in terms of the output tokens predicted per time step rather than its input tokens.

