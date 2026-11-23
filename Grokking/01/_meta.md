# _meta — machine-readable manifest

```meta
paper_id: 01
status: done
title: Grokking: Generalization Beyond Overfitting on Small Algorithmic Datasets
lang: zh
journal: arXiv 预印本
year: 2022
doi: 10.48550/arXiv.2201.02177
authors_short: Power 等
keywords: 延迟泛化; 小型算法数据集; 模运算; 数据效率; 权重衰减
one_liner: 模 97 除法中，训练准确率不到 1,000 步已接近满分，验证准确率接近 1,000,000 步才达到类似水平。
```

## Abstract

**背景：** 小型算法数据集可以把记忆、泛化与学习速度分开测量。

**方法：** 用同一个二元运算表的部分等式训练两层 Transformer，在剩余等式上验证；对比训练数据占比、运算和优化设置。

**结果：** 模 97 除法用 50% 数据训练时，训练准确率在不到 $10^3$ 步时已接近满分，而验证准确率接近 $10^6$ 步才达到类似水平。$S_5$ 乘积在训练占比约 25%–30% 时，每减少 1 个百分点，达到 99% 验证准确率所需步数的中位数约增加 40%–50%。

**结论：** 严重过拟合后仍可能通过继续训练获得泛化；在这些任务的部分数据量范围内，较少的数据需要更多优化。
