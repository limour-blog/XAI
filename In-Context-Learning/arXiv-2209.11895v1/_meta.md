# _meta

[论文索引](INDEX.MD)

```meta
paper_id: arXiv-2209.11895v1
status: done
title: In-context Learning and Induction Heads
lang: en
journal: Transformer Circuits Thread
year: 2022
doi: 10.48550/arXiv.2209.11895
authors_short: Olsson et al.
keywords: in-context learning; induction heads; phase change; mechanistic interpretability
one_liner: 34 个语言模型的实验把归纳头与上下文学习相变联系起来；小型纯注意力模型有直接消融证据。
```

## Abstract

**问题：** 归纳头执行 `[A][B] … [A] → [B]`。它们是否也解释语言模型随上下文增加而降低的预测损失？

**方法：** 追踪 34 个 Transformer 的训练快照，观察损失、归纳头评分，并比较架构干预、消融、案例与机制推导。

**结果：** 归纳头形成和上下文学习指标改善在早期训练相变中同步发生。小型纯注意力模型的归纳头消融大幅削弱上下文收益。

**范围：** 大型含 MLP 模型的证据主要是相关性、案例及跨尺度类比；尚不能确立归纳头解释其大部分上下文学习。
