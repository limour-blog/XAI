# DeepSeek-R1: Incentivizing Reasoning Capability in LLMs via Reinforcement Learning

> [合集索引](../INDEX.MD) · Level 1 · 2025 · [arXiv:2501.12948v2](https://arxiv.org/abs/2501.12948v2) · [本地主 TeX](../../TeX/Aha-Moment/arXiv-2501.12948v2/sn-article.tex) · [本地附录 TeX](../../TeX/Aha-Moment/arXiv-2501.12948v2/appendix.tex)

| 项目 | 内容 |
|---|---|
| 基座 | DeepSeek-V3-Base，671B MoE，单 token 激活 37B |
| 训练 | R1-Zero：不经初始 SFT，直接用 GRPO；R1：冷启动 SFT → 推理 RL → 拒绝采样与 SFT → 混合 RL |
| 代表结果 | R1-Zero：AIME 2024 pass@1 由 15.6% 到 77.9%；最终 R1 为 79.8% |

## 摘要（Abstract）

General reasoning represents a long-standing and formidable challenge in artificial intelligence. Recent breakthroughs, exemplified by large language models (LLMs) and chain-of-thought prompting, have achieved considerable success on foundational reasoning tasks. However, this success is heavily contingent upon extensive human-annotated demonstrations, and models' capabilities are still insufficient for more complex problems.

Here we show that the reasoning abilities of LLMs can be incentivized through pure reinforcement learning (RL), obviating the need for human-labeled reasoning trajectories. The proposed RL framework facilitates the emergent development of advanced reasoning patterns, such as self-reflection, verification, and dynamic strategy adaptation. Consequently, the trained model achieves superior performance on verifiable tasks such as mathematics, coding competitions, and STEM fields, surpassing its counterparts trained via conventional supervised learning on human demonstrations. Moreover, the emergent reasoning patterns exhibited by these large-scale models can be systematically harnessed to guide and enhance the reasoning capabilities of smaller models.

## 关键结论

- R1-Zero 的输出随训练变长，“wait”等反思用词更频繁；这是输出行为的证据，不直接揭示内部推理机制。
- R1 的阶段实验显示推理 RL 主要改善数学、编程等任务，末段混合 RL 对指令跟随与偏好评估的提升更明显；并非所有基准都优于 R1-Zero。
- 同为 Qwen 32B 路线，蒸馏模型 AIME 2024 pass@1 为 72.6%，直接 RL 的 Qwen2.5-32B-Zero 为 47.0%。

## 章节导航

- 前置信息：[作者与贡献](front-matter/authors-affiliations.md) · [元数据](_meta.md) · [引言](introduction/introduction.md)
- 方法：[GRPO](methods/1-grpo.md) · [R1-Zero 奖励](methods/2-zero-rewards.md) · [R1 阶段与奖励模型](methods/3-r1-pipeline.md) · [评估口径](methods/4-evaluation.md)
- 结果：[R1-Zero 涌现](results/1-zero-evolution.md) · [训练阶段](results/2-stage-results.md) · [标准基准](results/3-benchmarks.md) · [人类对照与偏好](results/4-human-evaluation.md) · [安全评估](results/5-safety.md) · [V3 对照](results/6-v3-comparison.md) · [新竞赛](results/7-new-competitions.md) · [数学分项](results/8-math-categories.md) · [推理长度](results/9-cot-length.md) · [代码题难度](results/10-coding-difficulty.md) · [蒸馏](results/11-distillation.md)
- 正文图表：[训练中的准确率与长度](figures/figure-1-zero-training.md) · [R1 流水线图](figures/figure-2-r1-pipeline.md) · [Zero 提示模板](tables/table-1-zero-template.md) · [Aha Moment 样例](tables/table-2-aha-moment.md) · [阶段结果](tables/table-3-stage-results.md)
- 补充图：[GRPO/PPO 示意](figures/supp-grpo.md) · [GRPO/PPO 实验](figures/supp-ppo-vs-grpo.md) · [RL 基础设施](figures/supp-rl-infrastructure.md) · [奖励投机](figures/supp-reward-hacking.md) · [语言一致性](figures/supp-language-consistency.md) · [MATH 难度](figures/supp-math-difficulty.md) · [反思词](figures/supp-reflection.md) · [人类基准](figures/supp-human-benchmarks.md) · [Arena 风格控制](figures/supp-arena-ranking.md) · [Arena 分项](figures/supp-arena-details.md) · [安全分类](figures/supp-safety-taxonomy.md) · [多语种安全](figures/supp-multilingual-safety.md) · [MMLU 分项](figures/supp-mmlu-comparison.md) · [数学竞赛分项](figures/supp-math-categories.md) · [测试时长度](figures/supp-test-time-scaling.md)
- 补充表：[RL 数据](tables/supp-rl-data.md) · [SFT 数据](tables/supp-sft-data.md) · [蒸馏配置](tables/supp-distill-config.md) · [训练成本](tables/supp-training-cost.md) · [主基准](tables/supp-main-benchmarks.md) · [公开安全基准](tables/supp-safety-eval.md) · [分项安全](tables/supp-safety-taxonomy.md) · [越狱鲁棒性](tables/supp-safety-robustness.md) · [V3 对照](tables/supp-v3-comparison.md) · [新竞赛](tables/supp-math-competitions.md) · [LiveCodeBench 难度](tables/supp-lcb-difficulty.md) · [蒸馏成绩](tables/supp-distill-eval.md) · [蒸馏对比 RL](tables/supp-distill-vs-rl.md) · [Qwen2-Math-7B-Zero](tables/supp-qwen-zero.md)
- 附录：[基座与 PPO](appendix/1-background.md) · [数据和训练细节](appendix/2-training-details.md) · [提示与样例](appendix/3-prompts-and-listings.md) · [评估样例定位](appendix/4-evaluation-examples.md)
- 讨论与资料：[关键发现、未成功的尝试与局限](discussion/discussion.md) · [伦理与安全声明](back-matter/ethics.md) · [权重、代码和数据](back-matter/open-resources.md) · [参考文献](references/references.md)
