# Tree of Thoughts: Deliberate Problem Solving with Large Language Models

> [合集索引](../INDEX.MD) · Level 1 · NeurIPS 2023 · [arXiv:2305.10601v2](https://arxiv.org/abs/2305.10601v2) · [本地主 TeX](../../TeX/Aha-Moment/arXiv-2305.10601v2/main.tex)

| 项目 | 内容 |
|---|---|
| 干预 | 推理时生成、评估和搜索语义级候选，不更新模型权重 |
| 实验 | GPT-4；24 点、约束式创意写作、5×5 迷你填字 |
| 代表结果 | 24 点：CoT 4.0%，ToT 宽度 1 为 45%，宽度 5 为 74% |

## 摘要（Abstract）

Language models are increasingly being deployed for general problem solving across a wide range of tasks, but are still confined to token-level, left-to-right decision-making processes during inference. This means they can fall short in tasks that require exploration, strategic lookahead, or where initial decisions play a pivotal role. To surmount these challenges, we introduce a new framework for language model inference, “Tree of Thoughts” (ToT), which generalizes over the popular “Chain of Thought” approach to prompting language models, and enables exploration over coherent units of text (“thoughts”) that serve as intermediate steps toward problem solving. ToT allows LMs to perform deliberate decision making by considering multiple different reasoning paths and self-evaluating choices to decide the next course of action, as well as looking ahead or backtracking when necessary to make global choices. Our experiments show that ToT significantly enhances language models’ problem-solving abilities on three novel tasks requiring non-trivial planning or search: Game of 24, Creative Writing, and Mini Crosswords. For instance, in Game of 24, while GPT-4 with chain-of-thought prompting only solved 4% of tasks, our method achieved a success rate of 74%. Code repo with all prompts: <https://github.com/princeton-nlp/tree-of-thought-llm>.

## 关键结论

- 24 点约 60% 的 CoT 样本在第一步就进入无解或无效状态；而对完整解答做 oracle best-of-100 也只有 49%。
- 写作的人评中 ToT 对 CoT 为 41 胜、38 平、21 负；填字的完整解题率由 CoT 的 1% 增至 20%。
- 收益依赖任务、模型和搜索预算；搜索并不等同于更多独立采样，也不是低成本替代。

## 章节导航

- 前置信息：[作者与机构](front-matter/authors-affiliations.md) · [元数据](_meta.md)
- 方法：[引言](introduction/introduction.md) · [IO、CoT 与自洽](methods/1-background.md) · [ToT 分解、评价与搜索](methods/2-tree-of-thoughts.md)
- 结果：[24 点](results/1-game-of-24.md) · [创意写作](results/2-creative-writing.md) · [迷你填字](results/3-mini-crosswords.md)
- 数据表：[任务概览](tables/table-1-task-overview.md) · [24 点](tables/table-2-game-of-24.md) · [填字](tables/table-3-crosswords.md) · [新任务](tables/table-4-new-tasks.md) · [24 点跨模型](tables/table-5-game-models.md) · [写作跨模型](tables/table-6-writing-models.md) · [24 点成本](tables/table-7-game-cost.md) · [写作成本](tables/table-8-writing-cost.md)
- 图：[1 方法示意](figures/figure-1-schematic.md) · [2 24 点流程](figures/figure-2-game-search.md) · [3 24 点扩展与错误](figures/figure-3-game-analysis.md) · [4 写作流程](figures/figure-4-writing-search.md) · [5 写作评分](figures/figure-5-writing-results.md) · [6 填字流程](figures/figure-6-crossword-search.md)
- 扩展：[新任务](appendix/1-new-tasks.md) · [GPT-3.5](appendix/2-gpt-3-5.md) · [成本](appendix/3-cost.md)
- 讨论与资料：[讨论和相关工作](discussion/discussion.md) · [代码、提示、轨迹与致谢](back-matter/reproducibility.md) · [参考文献](references/references.md)
