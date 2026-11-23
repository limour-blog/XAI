# In-Context Learning · 论文阅读索引

从论文摘要进入，再按论点、构造、图表或附录深入阅读。

| 论文 | 研究对象与主要发现 |
|---|---|
| [In-context Learning and Induction Heads](arXiv-2209.11895v1/INDEX.MD) | 在 34 个语言模型中追踪归纳头与训练相变；小型纯注意力模型有直接消融证据，大模型主要是相关证据。 |
| [Transformers Learn In-Context by Gradient Descent](arXiv-2212.07677v2/INDEX.MD) | 在合成回归中，一个线性自注意力层可精确实现一步梯度下降；部分多层模型更接近带曲率校正的 GD++。 |

**对照阅读：** 先看[归纳头的匹配与复制](arXiv-2209.11895v1/methods/2-induction-heads.md)，再看[注意力如何组装回归样本](arXiv-2212.07677v2/results/4-token-copying.md)与[一步梯度下降的构造](arXiv-2212.07677v2/methods/1-attention-and-gradient-descent.md)。前者用语言模型的 token 位置损失衡量上下文收益，后者用合成任务的查询预测误差检验内循环；两种实验不等同。
