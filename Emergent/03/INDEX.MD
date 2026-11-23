# Understanding the Emergence of Seemingly Useless Features in Next-Token Predictors

> [合集索引](../INDEX.MD) · Level 1 · [arXiv:2603.14087v1](https://arxiv.org/abs/2603.14087v1) · [本地全文](../../TeX/Emergent/arXiv-2603.14087v1/full.md)

| 项目 | 速览 |
|---|---|
| 问题 | 对当前下一 token 并非必要的内部特征，为什么会在训练中形成？ |
| 方法 | 按计算图拆分 3 类梯度，做训练消融与沿轨迹归因；用终点激活干预近似影响比 |
| 实验 | Majority、Conditioned Majority、OthelloGPT、TinyStories 与 Gemma 2 2B |

## 摘要（Abstract）

Trained Transformers have been shown to compute abstract features that appear redundant for predicting the immediate next token. We identify which components of the gradient signal from the next-token prediction objective give rise to this phenomenon, and we propose a method to estimate the influence of those components on the emergence of specific features. After validating our approach on toy tasks, we use it to interpret the origins of the world model in OthelloGPT and syntactic features in a small language model. Finally, we apply our framework to a pretrained LLM, showing that features with extremely high or low influence on future tokens tend to be related to formal reasoning domains such as code. Overall, our work takes a step toward understanding hidden features of Transformers through the lens of their development during training.

## 关键结论

- 预缓存由较后 token 的损失经注意力回传；电路共享让其他位置学到的计算在当前位置复用。两者都能提供直接学习以外的信号。
- OthelloGPT 对不改变下一步合法走法的棋格仍有表征，但较弱；TinyStories 的简单句法和原故事位置呈不同的梯度归因。
- Gemma 2 的 $Q(w)$ 估计的是终点附近的前后相对影响，不等同于训练轨迹归因，也不等同于对未来 token 的线性可解码性。

## 章节导航

- 前置信息：[作者与机构](front-matter/authors-affiliations.md) · [元数据](_meta.md)
- 方法：[§1 引言](introduction/introduction.md) · [§2 特征定义](methods/1-setup.md) · [§3.1 梯度分解](methods/2-gradient-decomposition.md) · [§3.2–3.3 消融与作用](methods/3-ablations.md) · [§3.4 训练轨迹归因](methods/4-feature-influence.md)
- 结果：[§4.1 玩具任务](results/1-toy-tasks.md) · [§4.2 OthelloGPT](results/2-othellogpt.md) · [§4.3 TinyStories](results/3-tinystories.md) · [§5.1 Gemma 2](results/4-gemma-pre-caching.md) · [§5.2 Look-ahead](results/5-look-ahead.md)
- 附录：[A 梯度分解证明](appendix/1-gradient-proof.md) · [B 归因细节](appendix/2-attribution.md) · [C 干预近似](appendix/3-intervention-proof.md) · [D 实验设置](appendix/4-experimental-details.md) · [E 补充结果](appendix/5-further-results.md)
- 正文图：[1 路径](figures/figure-1-gradient-paths.md) · [2 玩具探针](figures/figure-2-toy-probes.md) · [3 棋格](figures/figure-3-othello.md) · [4 句法与位置](figures/figure-4-tinystories.md) · [5 位置训练轨迹](figures/figure-5-position.md) · [6 Gemma 特征](figures/figure-6-gemma.md) · [7 前瞻](figures/figure-7-look-ahead.md)
- 附录图：[8 玩具任务归因](figures/figure-8-toy-influence.md) · [9 棋局训练](figures/figure-9-othello-training.md) · [10 棋局探针](figures/figure-10-othello-probes.md) · [11 核心棋格](figures/figure-11-othello-inner.md) · [12 外圈棋格](figures/figure-12-othello-outer.md) · [13 TinyStories 损失](figures/figure-13-text-loss.md) · [14 特征置信区间](figures/figure-14-text-influence.md) · [15 总分布](figures/figure-15-q-distribution.md) · [16 形式特征](figures/figure-16-formal.md) · [17 代码与数学](figures/figure-17-code-math.md) · [18 句法与结构](figures/figure-18-syntax-structure.md) · [19 导向生成](figures/figure-19-steering.md) · [20 Pearson 相关](figures/figure-20-pearson.md)
- 表：[1 玩具任务超参](tables/table-1-toy-hyperparameters.md) · [2 棋局超参](tables/table-2-othello-hyperparameters.md) · [3 TinyStories 超参](tables/table-3-text-hyperparameters.md) · [4 玩具准确率](tables/table-4-toy-accuracy.md) · [5 Wilcoxon](tables/table-5-wilcoxon.md) · [6 对数正态拟合](tables/table-6-log-normal.md) · [7 最低 Q](tables/table-7-low-q.md) · [8 最高 Q](tables/table-8-high-q.md) · [9 中段样本](tables/table-9-intermediate-q.md)
- 文末：[§6–7 相关工作与结论](discussion/discussion.md) · [项目、代码与致谢](back-matter/resources.md) · [参考文献](references/references.md)
