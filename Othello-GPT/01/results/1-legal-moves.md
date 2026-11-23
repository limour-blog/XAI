返回 [论文索引](../INDEX.MD) · 结果

# 2.3. Othello-GPT Usually Predicts Legal Moves

For each step of held-out games, the authors check whether the single highest-ranked prediction is a legal move conditioned on the preceding moves. Top-1 error was **0.01%** for synthetic training, **5.17%** for championship training, and **93.29%** for the untrained model.

To test transcript memorization, the authors trained a model on 20 million games from a skewed dataset. The openings are C5, D6, E3 and F4; they excluded the C5 branch (one quarter of the game tree). Top-1 error on test sequences from the excluded branch was **0.02%**. Different sequences can still reach the same board state, so this control excludes memorization of the input transcripts, not all previously reached states.

See [datasets](../methods/1-datasets.md) and [probe setup](../methods/3-probe-setup.md).
