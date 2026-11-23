返回 [论文索引](../INDEX.MD) · 方法

# 2–2.1. Language modeling of Othello game transcripts: Datasets

Othello is played on an 8 × 8 board. Players alternate placing black and white discs. A move must outflank opposing discs; the goal is to have the majority of the discs when play ends. The game tree is too large to memorize, yet the rules and board state are much simpler than chess. See [Figure 1](../figures/figure-1-othello-rules.md).

- **Championship:** 7,605 and 132,921 games from [Live Othello](https://www.liveothello.com/) and the [French Othello Federation](https://www.ffothello.org/), respectively. The combined games were randomly split 8:2 for training and validation. Expert players presumably played strategically.
- **Synthetic:** 20 million training games and 3,796,010 validation games. The paper describes constructing this dataset by uniformly sampling leaves from the Othello game tree; it contains legal play without an explicit strategy.

Compare [next-move legality](../results/1-legal-moves.md) and [latent saliency maps](../results/5-latent-saliency.md) for the contrasts between data sources.
