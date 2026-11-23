← [论文索引](../INDEX.MD)

# Footnotes


1 . Note that <sub>mec</sub>h<sub>an</sub>i<sub>s</sub>ti<sub>c</sub> i<sub>n</sub>t<sub>erpre</sub>t<sub>a</sub>bilit<sub>y</sub> is a subset of the broader field of i<sub>n</sub>t<sub>erpre</sub>t<sub>a</sub>bilit<sub>y</sub>, which encompasses many different methods for explaining the outputs of a neural network. Mechanistic interpretability is distinguished by a specific focus on trying to systematically characterize the internal circuitry of a neural net. [↩]

2. Note that induction heads don<sup>’</sup>t occur in 1 layer models, because they require a composition of attention heads in different layers. [↩]

3. Or sometimes <sub>me</sub>t<sub>a</sub>l<sub>earn</sub>i<sub>ng</sub>, although this term implicitly makes the stronger claim that the model is learning h<sub>ow</sub> to do a new ability (as opposed to “locating” an ability, i.e. learning <sub>w</sub>h<sub>a</sub>t it is supposed to do), an implication which is both controversial and not entirely precise in its meaning. [↩]

4. More specifically, induction heads seem to largely decouple A and B . While some induction heads may specialize on certain kinds of A s or B s, this significant decoupling of A and B means that they don't have a fixed table of bigram statistics they can update on, but rather can abstract to new patterns. [↩]

5. In practice, induction heads don't exhibit these properties perfectly, and our measurements give us a continuum, but there is a clear subset of heads which exhibit these properties with much greater than random chance. [↩]

6. By defining induction heads in terms of their behavior on repeated copies of random sequences, we can be confident that it's actually relying on induction rather than, say, a simple copying head that heuristically attends to previous tokens which could plausibly slot in well after the next token, even if that hasn<sup>’</sup>t occurred yet in the current context. [↩]

7. The simplest induction heads match just one preceding token. But we also often observe induction heads that perform a fuzzy match over several preceding tokens. [↩]

8. In mathematics, one sometimes thinks of a function as an infinite dimensional vector of the values it would give fo different inputs. For neural networks, this can be a nice way to abstract away the fact that functionally identical models can have very different parameter vectors. Of course, we can't directly represent these infinite dimensional vectors, bu we can approximate them by sampling. [↩]

9. Although see later discussion for a way in which a constant 0.4 nats can be viewed as a “larger” improvement for a morepowerful model, because attaining the same magnitude of improvement starting from a better baseline is more challenging. [↩]

1 0. As we'll see, many other curious phenomena occur during the phase change as well. [↩]

1 1 . That said, it<sup>’</sup>s also the case that aside from the experiments varying the dataset, all these models were trained on the same tokens in the same order [↩]

1 2. Of course, this passage is merely a single piece of anecdata, shown here to provide a qualitative intuition rather than meant as systematic evidence. For a more comprehensive analysis of the observed behavioral change before and after the phase change, consult the “ablation to before-and-after vector” analyses in the Model Analysis Table [↩]

1 3. Some bits of information are harder to learn than others. For example, near the start of training, the model can achieve a significant decrease in loss with simple approaches such as memorizing bigram statistics. But later in training all the low hanging fruit has been plucked, and the model must learn more sophisticated algorithms such as induction heads, which is likely harder to learn yet results in fewer bits of information. In today<sup>’</sup>s state of the art models, such as GPT-3, we observe complex capabilities such as addition, and we can imagine future models approaching near-perfect loss might need human-level understanding of language and beyond to get those last few fractions of a bit. So the <sub>re</sub>l<sub>a</sub>ti<sub>ve</sub> loss[16] between token 50 and token 500 likely represents harder and harder bits over the course of training. [↩]

1 4. It is still a mystery why these forces of increased capacity for in-context learning and increasing difficulty of marginal bits would so <sub>exac</sub>tl<sub>y</sub> balance, and this seems a promising avenue of future research. Perhaps there is not, in fact, much

overlap in the information that could be gained from both in-context learning and other approaches, so th<sub>ese</sub> bits do not get harder with time. We'll revisit this in the Discussion. [↩]

1 5. Why do induction heads require composition? In an induction head, where the head attends must be a function of the token before the token it attends to. But an individual attention head computes attention scores only from the source and destination token. Without using information written by a second earlier attention head, the score from the attended token can<sup>’</sup>t be a function of the token that precedes it. [↩]

1 6. The key vector for the first token is unchanged. [↩]

1 7. In fact, ablating most other attention heads appears to i<sub>ncrease</sub> in-context learning. At first, that seems kind of crazy: how could damaging the model make it b<sub>e</sub>tt<sub>er</sub> at in-context learning? It appears that some tokens can be predicted with both "normal prediction" and in-context learning. If ablating a head makes the model bad at "normal prediction", in context learning can predict more tokens that otherwise wouldn't be predicted, and in-context learning score as we've defined it increases. [↩]

1 8. Note that the cost of a full set of ablations scales superlinearly with model size at ${ \cal O } ( N ^ { 1 . 3 3 } )$ , since there are $O ( N ^ { 0 . 3 3 } )$ heads and each ablation is where is the number of parameters. The base cost of an ablation is also non-trivial,O(N) N since we're evaluating each ablation on 10,000 examples, for each training checkpoint. [↩]

1 9. In attention-only models, the logits can be expressed (up to a rescaling due to LayerNorm) as a sum of terms from each attention head, along with a "direct path term" to the the token embedding (see our previous paper). The direct path term is solely a function of the present token, so it can't contribute to in-context learning. That means that all in-context learning must ultimately originate with attention heads, and since the relationship is almost linear, ablations (with frozen attention patterns) are a principled way to measure their contribution. [↩]

2 0. Why is ablating attention heads harder to reason about if they can interact with MLP layers? At a high-level, the issue is that in-context learning is a complicated function of which heads are ablated, rather than a sum of their contributions. But it may be helpful to consider specific examples. One possibility is that ablating a head might shift the statistics of an MLP layer and "break" neurons by shifting their effective bias, without actually having a meaningful role. Another possibility is that an important MLP layer mechanism relies on two attention heads, but can function reasonably well with one if the other is albated. [↩]

2 1 . We compute this by taking the value vector produced at each position, weighting it by the attention matrix, and multiplying it by $W _ { O }$ and the unembedding, and selecting the logit value for the corresponding token. Note that we first normalise the vector of logits to have zero mean, as adding a constant to every argument in a softmax has no effect. [↩]

2 2. For example, a special case of translating from English to another language is translating English to itself, which is precisely the same as literal copying. [↩]

2 3. The only other potential contender for driving in-context learning in two-layer attention only models would be basic copying heads. However, basic copying heads also exist in one-layer models, which don't have the greatly increased in context learning we see in two-layer models. Further, induction heads just seem conceptually more powerful. [↩]

24. Note that the attended token is only ignored when calculating the <sub>a</sub>tt<sub>en</sub>ti<sub>on pa</sub>tt<sub>ern</sub> through the QK-circuit. It is extremely important for calculating the head<sup>’</sup>s <sub>ou</sub>t<sub>pu</sub>t through the OV-circuit! As observed in our previous work, the parts of the head that calculate the attention pattern, and the output if attended to, are separable and are often useful to consider independently. [↩]

2 5. Instead, they use a slightly unusual positional mechanism similar to Press <sub>e</sub>t <sub>a</sub>l. [↩][17]

2 6. Note that this is different to the small models, which have 200 snapshots saved at linear intervals. As the full-scale models have only 14 or 15 snapshots, this makes it harder to judge the shape of the curves as confidently as for small models. [↩]

2 7. Around token 100, there's a regime where small models reduce their loss very slightly more per token than large models. We interpret this as the small models picking up low-hanging fruit that the large models already got in the very early context. [↩]

2 8. In fact, small models gain slightly more in the mid-context, catching up a tiny bit with large models, but it's a smal effect. [↩]

2 9. The fact that this is possible at all is a surprising application of the insight in our previous work that the calculation of each attention head<sup>’</sup>s attention pattern and output vector is <sub>separa</sub>bl<sub>e</sub>, that is, implemented by different circuits consisting of different sets of parameters which may be run and studied in isolation [↩]

30. As an interesting aside, we note that with the attention pattern frozen the action of each head is purely linear, which means that in an attention-only model, a pattern-preserving ablation is equivalent to subtracting all terms containing the ablated head from the output logits. See our previous work for further exploration of the implications of this. This does not hold in more complex models, due to the non-linearity introduced by MLPs [↩]

3 1 . It would<sup>’</sup>ve been better if we had used a start of sequence token for the copying head evaluator as well, but we omitted it by mistake. Without the “start of sequence” token, some heads that were doing prefix matching on real data would get anomalously low scores on our test sequences [↩]

