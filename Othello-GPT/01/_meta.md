返回 [论文索引](INDEX.MD)

# _meta — machine-readable manifest

```meta
paper_id: 01
status: done
title: Emergent world representations: Exploring a sequence model trained on a synthetic task
lang: en
journal: ICLR 2023
year: 2023
doi:
arxiv: 2210.13382v5
authors_short: Li et al.
keywords: Othello-GPT; board state; nonlinear probing; activation intervention; latent saliency
one_liner: Othello-GPT 的棋盘状态可被探针读出（黑／白／空分类最低错误率 1.7%）；改写该状态会改变合法落子的预测。
```

## Abstract

**Background:** The authors ask whether sequence models learn internal representations of the data-generating process, or just memorize surface statistics. Othello provides a controlled test with known game rules and a hidden board state.

**Methods:** An eight-layer GPT model predicts moves after training solely on game transcripts. Linear and two-layer MLP probes decode individual tile states. Counterfactual activation edits target a tile across multiple layers, and changes in predicted move probabilities are used to build latent saliency maps.

**Results:** Synthetic training produces 0.01% top-1 illegal moves; holding out an entire opening branch produces 0.02% error on that branch. On the synthetic model, the best tested linear and nonlinear black/white/empty probes have errors of 20.4% and 1.7%, respectively. At the best intervention setting, legal-move-set errors drop from 2.68 to 0.12 for natural positions and from 2.59 to 0.06 for unreachable positions, against the null baselines.

**Conclusion:** Evidence supports an internal board-state representation with a causal role in next-move prediction. The saliency patterns differ between models trained on synthetic play and expert championship games.
