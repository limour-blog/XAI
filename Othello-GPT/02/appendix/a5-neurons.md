返回 [论文索引](../INDEX.MD) · 附录

# A.5. Neurons writing to the sentiment direction in GPT2-small

The cosine similarity between MLP neuron output vectors and the sentiment direction has heavy tails ([Figure A.10](../figures/figure-a-10-neuron-similarity.md)). Example neurons found using Neuroscope:

- [L3N1605](https://neuroscope.io/gpt2-small/3/1605.html): “hesitate” after a negation.
- [L6N828](https://neuroscope.io/gpt2-small/6/828.html): “however” or “on the other hand” after negative text.
- [L5N671](https://neuroscope.io/gpt2-small/5/671.html): negative words after a contracted “not”.
- [L6N1237](https://neuroscope.io/gpt2-small/6/1237.html): “but” after “not bad”.

Using direct logit attribution, compare `I would not hesitate` with `I would always hesitate` for L3N1605. L1H0, L3H10, L3H11, and MLP2 account for important parts of the difference. Within MLP2, L2N1154 responds to negators; it fires at `not` in the first prompt and at `hesitate` in the second. L1H0 attends from `hesitate` to its preceding token if it is `not`, but not if it is `always`. These examples suggest sentiment-relevant components communicate via a shared direction, with possible applications to studying negation.
