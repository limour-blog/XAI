> [论文索引](../INDEX.MD) · 正文 Experiment

# R1 分阶段结果

[阶段对照表](../tables/table-3-stage-results.md)与[流水线图](../figures/figure-2-r1-pipeline.md)区分多个检查点。

- Zero → Dev1：IF-Eval 46.6→71.7、ArenaHard 53.6→77.0，但 AIME 2024 77.9→59.0。
- Dev1 → Dev2：推理 RL 后，AIME 2024 59.0→74.0、LiveCodeBench 57.5→63.5；AlpacaEval 2.0 变化较小（50.1→55.8）。
- Dev2 → Dev3：扩大 SFT 数据后，Aider-Polyglot 25.6→44.8，AlpacaEval 2.0 55.8→62.1。
- Dev3 → R1：AlpacaEval 2.0 62.1→87.6，ArenaHard 75.6→92.3。AIME 2024 最终 79.8，GPQA Diamond 的 71.5 仍低于 Zero 的 75.8。

[按代码题难度分层](10-coding-difficulty.md)显示容易题接近饱和，变化主要来自中、难题。
