# Chain-of-Thought Prompting Elicits Reasoning in Large Language Models

> [合集索引](../INDEX.MD) · Level 1 · NeurIPS 2022 · [arXiv:2201.11903v6](https://arxiv.org/abs/2201.11903v6) · [本地主 TeX](../../TeX/Chain-of-Thought/arXiv-2201.11903v6/neurips_2022.tex)

| 项目 | 内容 |
|---|---|
| 比较 | 标准少样本提示 vs. 含中间步骤的少样本提示；不微调 |
| 评估 | 算术、常识、符号推理；贪心解码 |
| 代表结果 | PaLM 540B 在 GSM8K 上从 17.9% 到 56.9%（8 个示例） |

## 摘要（Abstract）

We explore how generating a *chain of thought*—a series of intermediate reasoning steps—significantly improves the ability of large language models to perform complex reasoning. In particular, we show how such reasoning abilities emerge naturally in sufficiently large language models via a simple method called *chain-of-thought prompting*, where a few chain of thought demonstrations are provided as exemplars in prompting.

Experiments on three large language models show that chain-of-thought prompting improves performance on a range of arithmetic, commonsense, and symbolic reasoning tasks. The empirical gains can be striking. For instance, prompting a PaLM 540B with just eight chain-of-thought exemplars achieves state-of-the-art accuracy on the GSM8K benchmark of math word problems, surpassing even finetuned GPT-3 with a verifier.

## 关键结论

- 收益随模型和任务而变；复杂多步题通常比单步题受益更多。
- 仅增加占位符，或将推理放在答案之后，不能复现 GSM8K 的提升。
- 符号任务能外推到更长序列，但不等于任意长度泛化，也不保证输出推理忠实。

## 章节导航

- 前置信息：[作者与机构](front-matter/authors-affiliations.md) · [元数据](_meta.md)
- 方法：[思维链提示](methods/1-chain-of-thought-prompting.md) · [实验设置](methods/2-experimental-setup.md)
- 结果：[算术](results/1-arithmetic.md) · [消融](results/2-ablation.md) · [鲁棒性](results/3-robustness.md) · [常识](results/4-commonsense.md) · [符号](results/5-symbolic.md)
- 数据表：[1 主模型算术](tables/table-1-flagship-arithmetic.md) · [2 全模型算术](tables/table-2-all-arithmetic.md) · [3 MAWPS 子集](tables/table-3-mawps.md) · [4 常识](tables/table-4-commonsense.md) · [5 符号](tables/table-5-symbolic.md) · [6 算术消融](tables/table-6-arithmetic-ablation.md) · [7 常识与符号消融](tables/table-7-commonsense-symbolic-ablation.md) · [8 算术评估集与题例](tables/table-8-arithmetic-datasets.md)
- 图：[1 提示对照](figures/figure-1-prompting.md) · [2 GSM8K](figures/figure-2-gsm8k.md) · [3 任务示例](figures/figure-3-exemplars.md) · [4 算术曲线](figures/figure-4-arithmetic.md) · [5 消融](figures/figure-5-ablation.md) · [6 鲁棒性](figures/figure-6-robustness.md) · [7 常识曲线](figures/figure-7-commonsense.md) · [8 符号曲线](figures/figure-8-symbolic.md) · [9 错误类型](figures/figure-9-palm-errors.md) · [10 修正案例](figures/figure-10-palm-fixes.md) · [11 示例数量](figures/figure-11-shot-count.md)
- 讨论与附录：[讨论与结论](discussion/discussion.md) · [FAQ 与错误分析](appendix/1-faq-and-errors.md) · [输入输出与完整提示定位](appendix/2-exemplars-and-prompts.md) · [算术主提示（8 个原文示例）](appendix/3-math-word-problem-prompt.md) · [复现、数据和版本](back-matter/reproducibility.md) · [参考文献](references/references.md)
