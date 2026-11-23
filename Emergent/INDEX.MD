# Emergent：大模型的能力涌现、度量效应与特征形成

> 渐进式披露 · Level 0

| # | 论文 | 一句话结论 | 入口 |
|---|---|---|---|
| 01 | Emergent Abilities of Large Language Models | 综述 5 个模型家族的 8 个少样本实例：部分任务在所用指标下从近随机跃升至明显超随机。 | [论文索引](01/INDEX.MD) |
| 02 | Are Emergent Abilities of Large Language Models a Mirage? | 固定模型输出，换指标或提高统计分辨率可消除部分跃升；人工标注案例中超过 92% 集中于两个指标。 | [论文索引](02/INDEX.MD) |
| 03 | Understanding the Emergence of Seemingly Useless Features in Next-Token Predictors | 将训练梯度分为 3 类，解释下一 token 预测不需要、却仍可在模型内部学到的特征。 | [论文索引](03/INDEX.MD) |

**阅读顺序：** 先看 01 如何定义和记录任务分数的跃升，再读 02 如何区分输出变化与评分变化。03 讨论的是训练过程中内部表征的形成，不是在检验前两篇的任务规模阈值。

01、02 由 TeX 原文直接编写：保留英文摘要，正文按节用中文整理，原图或绘图源码可从图页追溯。03 的本地来源为既有 `full.md` 与图片，直接分层整理。原始文件未改动。
