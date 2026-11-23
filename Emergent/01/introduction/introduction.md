> [返回论文索引](../INDEX.MD) · §1

# 引言

扩展语言模型往往改善下游表现和样本效率。交叉熵损失有跨越七个数量级以上的经验缩放规律，但部分下游曲线在小规模段没有明显改善，之后突然高于随机水平。作者借用 Anderson 的 “More Is Different” 视角，将涌现理解为系统的定量变化带来定性行为变化。

本文聚焦预训练 Transformer，不试图追溯更早的所有 NLP 涌现现象。它汇总[少样本任务](../results/1-few-shot-tasks.md)与[增强策略](../results/2-augmented-prompting.md)两类文献证据，并追问两个问题：什么导致所报告的跃升，继续扩大规模是否会带来新能力？判断口径见[定义](../methods/1-emergence-definition.md)。
