返回 [论文索引](../INDEX.MD) · 引言

# 1. Introduction

Language models trained to predict the next word can solve logic puzzles and write basic code. It is unclear whether this ability comes from surface statistics or from representations of the process that generates the data. Reliance on spurious correlations can produce out-of-distribution failures. Prior work found internal information about color, direction, and boolean states; work on chess transcripts found that a language model predicts legal moves and appears to track the board, but did not investigate the form of its representation.

## 1.1 The game of Othello as testbed for interpretability

Othello provides a controlled setting: the world is the board, the data are sequences of moves, and the rules are simpler than chess. Othello-GPT is trained to continue transcripts, not explicitly to win or make strategic moves. It receives only tokens for disc placement, with no rules or board states provided during training.

The experiments ask what the model learns beyond predicting legal moves. Probes recover board state from activations; nonlinear probes outperform the tested linear probes. Counterfactual interventions test whether that information affects predictions, and latent saliency maps attribute move predictions to board positions rather than input tokens. See [the probing setup](../methods/3-probe-setup.md), [intervention technique](../methods/4-intervention.md), and [latent saliency maps](../results/5-latent-saliency.md).
