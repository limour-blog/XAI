# _meta — machine-readable manifest

```meta
paper_id: 02
status: done
title: Progress measures for grokking via mechanistic interpretability
lang: zh
journal: ICLR
year: 2023
doi: 10.48550/arXiv.2301.05217
authors_short: Nanda 等
keywords: 延迟泛化; 机制可解释性; 模加法; 傅里叶乘法; 进度指标
one_liner: 模 113 加法中，5 个关键频率构成的泛化电路在约 10,000 个 epoch 的测试准确率跃升前已逐步形成。
```

## Abstract

**背景：** 测试准确率可以突然上升，单看原始学习曲线难以判断这之前发生了什么。

**方法：** 在模 113 加法上训练单层 Transformer，通过分解权重、分析激活、进行傅里叶消融，逆向分析模型使用的算法，再从该机制构造进度指标。

**结果：** 主模型在五个关键频率上编码输入并组合旋转。限制损失和排除损失在原始测试曲线约 10,000 个 epoch 的跃升之前就已显著变化，把训练过程区分为记忆、电路形成和清理。

**结论：** 在这组实验中，准确率跃升是泛化电路逐渐增强、记忆成分随后减弱的结果。进度指标可以回看这一变化，但还不能预测新任务的跃升时间。
