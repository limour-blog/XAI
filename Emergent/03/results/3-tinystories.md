> [返回论文索引](../INDEX.MD) · §4.3

# TinyStories：局部句法与篇章位置的信号不同

GPT-2-like 小模型在 TinyStories v2 的随机 64-token 子串上训练。探查 10 种 POS、10 种依存标签，以及 token 在原故事中的归一化位置。Myopic 与标准训练损失分别为 $3.29\pm0.02$ 和 $2.53\pm0.10$。

句法探针在两种训练下表现差异不大，同一层的直接影响大于预缓存影响；原故事位置的中间层出现相反结果。位置特征的预缓存影响在训练中途开始上升。原文据此区分简单句法与可能涉及更高层文本结构的特征。

[图 4 探针与影响](../figures/figure-4-tinystories.md) · [图 5 位置](../figures/figure-5-position.md) · [图 13 损失](../figures/figure-13-text-loss.md) · [图 14 区间](../figures/figure-14-text-influence.md) · [表 3 超参](../tables/table-3-text-hyperparameters.md) · [表 5 检验](../tables/table-5-wilcoxon.md)
