# _meta

[论文索引](INDEX.MD)

```meta
paper_id: arXiv-2212.07677v2
status: done
title: Transformers Learn In-Context by Gradient Descent
lang: en
journal: ICML 2023 (PMLR)
year: 2023
doi: 10.48550/arXiv.2212.07677
authors_short: von Oswald et al.
keywords: Transformers; in-context learning; mechanistic interpretability; mesa-optimization
one_liner: 合成回归中，单层线性自注意力可实现一步梯度下降；多层结果更接近带曲率校正的 GD++。
```

## Abstract

**问题：** Transformer 的前向传播能否用梯度下降实现上下文学习？

**方法：** 构造单头线性注意力的权重，证明其与平方损失的一步 GD 等价，再用无噪声合成回归比较预测、查询导数、分布外行为与权重插值。

**结果：** 训练的单层近似复现构造；多层在实验中表现得更像带输入依赖曲率校正的 GD++。MLP 特征上的一步更新支持正弦波回归。从交替 token 构造输入和目标配对的一层可与后续执行更新的层组合。

**范围：** 训练验证限于小型 Transformer 与简单回归任务。
