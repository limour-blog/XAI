# Are Emergent Abilities of Large Language Models a Mirage?

> [合集索引](../INDEX.MD) · Level 1 · NeurIPS 2023 · [arXiv:2304.15004v2](https://arxiv.org/abs/2304.15004v2) · [主 TeX](../../TeX/Emergent/arXiv-2304.15004v2/00_main.tex)

| 项目 | 速览 |
|---|---|
| 研究设计 | 数学示例、固定输出重评分、BIG-Bench 元分析、视觉受控示例 |
| 主要比较 | 整串准确率 vs. token 编辑距离；Multiple Choice Grade vs. Brier Score |
| 核心发现 | 手工标注的 BIG-Bench 涌现案例中，>92% 由两个指标报告；不是“所有涌现都不可能” |

## 摘要（Abstract）

Recent work claims that large language models display *emergent abilities*, abilities not present in smaller-scale models that are present in larger-scale models. What makes emergent abilities intriguing is two-fold: their *sharpness*, transitioning seemingly instantaneously from not present to present, and their *unpredictability*, appearing at seemingly unforeseeable model scales.

Here, we present an alternative explanation for emergent abilities: that for a particular task and model family, when analyzing fixed model outputs, emergent abilities appear due the researcher’s choice of metric rather than due to fundamental changes in model behavior with scale. Specifically, nonlinear or discontinuous metrics produce apparent emergent abilities, whereas linear or continuous metrics produce smooth, continuous, predictable changes in model performance.

We present our alternative explanation in a simple mathematical model, then test it in three complementary ways: we (1) make, test and confirm three predictions on the effect of metric choice using the InstructGPT/GPT-3 family on tasks with claimed emergent abilities, (2) make, test and confirm two predictions about metric choices in a meta-analysis of emergent abilities on BIG-Bench; and (3) show how to choose metrics to produce never-before-seen seemingly emergent abilities in multiple vision tasks across diverse deep networks.

Via all three analyses, we provide evidence that alleged emergent abilities evaporate with different metrics or with better statistics, and may not be a fundamental property of scaling AI models.

## 关键结论

- 整串评分可以把连续的逐 token 改善压到零附近，增加测试样本后，小模型的非零准确率可辨认。
- 对同一批 GPT 输出，改用 token 编辑距离，四、五位答案的跃升变为平滑改善。
- 在分析的 LaMDA 任务中，用 Brier Score 替代 Multiple Choice Grade，跃升不再出现。

## 章节导航

- 前置信息：[作者与机构](front-matter/authors-affiliations.md) · [元数据](_meta.md)
- 理论：[§1 引言](introduction/introduction.md) · [§2 数学模型](methods/1-analytical-model.md)
- 算术：[§3 换指标](results/1-arithmetic-metric.md) · [§3 提高分辨率与答案长度](results/2-arithmetic-resolution.md)
- BIG-Bench：[§4 指标集中度](results/3-big-bench-metrics.md) · [§4 LaMDA 重评分](results/4-lamda-brier.md)
- 视觉：[§5 CIFAR100](results/5-cifar100.md) · [§5 Omniglot](results/6-omniglot.md) · [B MNIST](appendix/2-mnist.md)
- 讨论与补充：[§6 相关工作](discussion/related-work.md) · [§7 讨论](discussion/discussion.md) · [A 序列指标近似](appendix/1-sequence-metrics.md) · [参考文献](references/references.md)
- 图：[1 既有案例](figures/figure-1-prior-emergence.md) · [2 数学示例](figures/figure-2-analytical-model.md) · [3 算术重评分](figures/figure-3-arithmetic-metrics.md) · [4 算术分辨率](figures/figure-4-arithmetic-resolution.md) · [5 BIG-Bench 指标分布](figures/figure-5-big-bench-metrics.md) · [6 LaMDA 重评分](figures/figure-6-lamda-brier.md) · [7 CIFAR100](figures/figure-7-cifar100.md) · [8 Omniglot](figures/figure-8-omniglot.md) · [9 ROUGE-L-Sum](figures/figure-9-rouge-l-sum.md) · [10 MNIST](figures/figure-10-mnist.md)
