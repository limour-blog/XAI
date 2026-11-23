← [论文索引](../INDEX.MD)

# 1. Introduction：两种时间尺度上的学习

上下文学习（in-context learning）指模型在不更新自身权重的情况下，利用输入序列中的示例调整预测。本文把 Transformer 的参数训练看作元学习的**外循环**：跨任务调整共享参数 $\theta$。训练后的前向传播则可能执行**内循环**：把当前上下文组织成任务数据，并在激活中实现对任务特定模型的更新。两者不能混为一谈；内循环中的回归权重 $W$ 不等于 Transformer 的参数 $\theta$。

**假设 1（原文的研究假设）：** 用自回归任务训练 Transformer 时，前向传播中的上下文学习可由基于梯度的优化实现，所优化的是通过上下文数据构造的隐式自回归损失。主要实验证据来自合成回归任务，外循环只在最后的查询位置计损，不能把假设直接当作大语言模型的一般定理。

作者先构造一个可执行一步 GD 的单头线性注意力层，再比较训练所得权重和构造；随后考察深层曲率校正、MLP 特征上的非线性回归，以及第一层从分离的 token 组装样本的能力。该视角与 fast weights、MAML 的输出层适配及 mesa-optimization 相联系。[图 1：元学习与注意力](../figures/figure-1-hypothesis.md)。

[复现实验 notebook（Google Research）](https://github.com/google-research/self-organising-systems/tree/master/transformers_learn_icl_by_gd)
