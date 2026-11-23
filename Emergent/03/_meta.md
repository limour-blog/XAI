# _meta — 论文元数据

```meta
paper_id: 03
status: done
title: Understanding the Emergence of Seemingly Useless Features in Next-Token Predictors
lang: en
journal: arXiv
year: 2026
doi:
authors_short: Rofin et al.
keywords: next-token prediction; pre-caching; circuit sharing; developmental interpretability
one_liner: 将训练梯度分为 3 类，解释下一 token 预测不需要、却仍可在模型内部学到的特征。
```

## Abstract

**Background:** Transformer representations can encode features unnecessary for predicting the immediate next token. **Methods:** The authors decompose gradients into direct, pre-cached and shared paths, ablate paths in small models, integrate their contribution along training and estimate relative delayed influence near a pretrained checkpoint by intervention. **Results:** The analysis explains weak but detectable representations of Othello squares irrelevant to the next move, distinguishes syntax from story position in TinyStories and finds formal-domain features overrepresented at the extremes of the Gemma 2 ratio. **Conclusion:** Feature formation is not limited to direct next-token gradients; terminal interventions are not a substitute for observing the training trajectory.

[论文索引](INDEX.MD)
