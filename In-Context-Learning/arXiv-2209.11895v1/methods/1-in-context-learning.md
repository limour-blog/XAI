← [论文索引](../INDEX.MD)

# In-context Learning: definition and score

> **符号约定：** 定义与附录写作 $L_{500}-L_{50}$；[论据 1](../results/1-phase-change.md) 报告正的改善幅度时使用反向差值 $L_{50}-L_{500}$。两处不是同一个符号方向。

In modern language models, tokens later in the context are easier to predict than tokens earlier in the context. As the context gets longer, loss goes down. In some sense this is just what a sequence model is designed to do (use earlier elements in the sequence to predict later ones), but as the ability to predict later tokens from earlier ones gets better, it can increasingly be used in interesting ways (such as specifying tasks, giving instructions, or asking the model to match a pattern) that suggest it can usefully be thought of as a phenomenon of its own. When thought of in this way, it is usually referred to as in-context learning. 3

Emergent in-context learning was noted in GPT-2 and gained significant attention in GPT-3 .[10] [1] Simply by adjusting a “prompt”, transformers can be adapted to do many useful things without retraining, such as translation, question-answering, arithmetic, and many other tasks. Using “prompt engineering” to leverage in-context learning became a popular topic of study and discussion .[11, 12]

At least two importantly different ways of conceptualizing and measuring in-context learning exist in the literature. The first conception, represented in Brown <sub>e</sub>t <sub>a</sub>l., focuses on f<sub>ew</sub>-<sub>s</sub>h<sub>o</sub>t l<sub>earn</sub>i<sub>ng</sub> of[1] specific tasks. The model is prompted with several instances of some “task” framed in a nexttoken-prediction format (such as few-digit addition, or English-to-French translation). The second conception of in-context learning, represented in Kaplan <sub>e</sub>t <sub>a</sub>l. , focuses on observing the loss at[13] different t<sub>o</sub>k<sub>en</sub> i<sub>n</sub>di<sub>ces</sub>, in order to measure how much better the model gets at prediction as it receives more context. The first conception can be thought of as a micro perspective (focusing on specific tasks), where as the second conception can be seen as a macro perspective (focusing on general loss, which on average correlates with these tasks).

The “few-shot learning” conception of in-context learning has tended to receive greater community attention. The ability to do many different tasks with one large model, even without further finetuning, is a notable change to the basic economics of model training. Moreover, it gives evidence of wide-ranging general capabilities and the ability to adapt on the fly, which nudges us to re-examine what it means for a model to “understand” or to “reason”.

However, for the purposes of this work, we focus instead on the Kaplan <sub>e</sub>t <sub>a</sub>l. conception: d<sub>ecreas</sub>i<sub>ng</sub> l<sub>oss</sub> at i<sub>ncreas</sub>i<sub>ng</sub> t<sub>o</sub>k<sub>en</sub> i<sub>n</sub>di<sub>ces</sub>. We do so because it's a more general framing of the phenomenon than “few-shot learning”. A drawback of this definition is it fails to isolate specific behaviors of interest. At the same time, it allows us to measure models<sup>’</sup> overall ability to learn onthe-fly from the context, without depending on our specific choices of “task”. We<sup>’</sup>ll also see that, starting from this definition, we are <sub>a</sub>l<sub>so</sub> able to study a couple classic few-shot learning examples (see Argument 4).

Throughout this work we compute a simple heuristic measure of in-context learning:

In-context learning score: the loss of the 500th token in the context minus the average loss of the 50th token in the context, averaged over dataset examples.

We chose the 500th and 50th token indices somewhat arbitrarily. The 500th token is near the end of a length-512 context, and the 50th token is far enough into the context that some basic properties of the text have been established (such as language and document type) while still being near the start. We will also show that picking different numbers here does not change our conclusions.

Finally, it is worth noting that in-context learning is of potentially special relevance to safety. Incontext learning makes it harder to anticipate how a model might behave after a long context. In the longer run, concepts such as mesa-optimization or inner-alignment postulate that meaningful[14] learning or optimization could occur at test time (without changing the weights). In-context learning would be an obvious future mechanism for such hidden optimization to occur, whether or not it does so today. Thus, studying in-context learning seems valuable for the future.

(See Related Work for more on in-context learning, and Discussion for more on the connection to safety.)

