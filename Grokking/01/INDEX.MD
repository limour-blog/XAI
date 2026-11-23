# Grokking: Generalization Beyond Overfitting on Small Algorithmic Datasets

> **论文 01 · 渐进式披露 Level 1**
> 本页索引中文导读和附录。原导读与附录合并归档于 [`full.md`](full.md)；英文论文版本见[来源与版本](front-matter/editorial.md)。

## 速览（At a Glance）

| 项目 | 内容 |
| --- | --- |
| 研究类型 | 小型算法数据上的控制实验 |
| 研究模型 | 两层 decoder-only Transformer |
| 实验变量 | 运算类型、训练集占比、优化器和正则化 |
| 主要指标 | 训练和验证损失、准确率及达到 99% 验证准确率的步数 |
| 核心发现 | 模 97 除法中，训练与验证达到近满分相差约三个数量级的更新步数 |
| 来源 | [arXiv:2201.02177v1](https://arxiv.org/abs/2201.02177v1)（2022） |

## 摘要（Abstract）

**背景：** 小型算法数据集可以把记忆、泛化与学习速度分开测量。

**方法：** 用同一个二元运算表的部分等式训练两层 Transformer，在剩余等式上验证；对比训练数据占比、运算和优化设置。

**结果：** 模 97 除法用 50% 数据训练时，训练准确率在不到 $10^3$ 步时已接近满分，而验证准确率接近 $10^6$ 步才达到类似水平。$S_5$ 乘积在训练占比约 25%–30% 时，每减少 1 个百分点，达到 99% 验证准确率所需步数的中位数约增加 40%–50%。

**结论：** 严重过拟合后仍可能通过继续训练获得泛化；在这些任务的部分数据量范围内，较少的数据需要更多优化。

## 核心结论（Key Findings）

- 模除法典型曲线不需要权重衰减；在 $S_5$ 乘积的消融中，权重衰减可显著提高数据效率。
- 输出层权重的 t-SNE 投影显示模加法的环状结构和置换群的陪集结构，但投影本身不能确定模型的计算算法。

## 关键词（Keywords）

[延迟泛化 · 小型算法数据集 · 模运算 · 数据效率 · 权重衰减](front-matter/keywords.md)

## 目录导航（Level 2 → Level 3）

### 前置信息（`front-matter/`）

- [来源与版本](front-matter/editorial.md) — 论文信息
- [作者与机构](front-matter/authors-affiliations.md) — 论文信息
- [关键词](front-matter/keywords.md) — 中文导读索引词

### 引言（`introduction/`）

- [把泛化变成填运算表](introduction/introduction.md) — §1 · Introduction
- [相关工作：算法基准与梯度噪声](introduction/related-work.md) — 附录 A.3 · Related work

### 方法（`methods/`）

- [二元运算任务与评估](methods/1-binary-operation-task.md) — §2 · Method
- [运算范围](methods/2-binary-operations.md) — 附录 A.1 · Binary operations
- [模型与优化配置](methods/3-model-and-optimization.md) — 附录 A.1 · Model and optimization

### 结果（`results/`）

- [过拟合之后的延迟泛化](results/1-generalization-beyond-overfitting.md) — §3.1 · Generalization beyond overfitting
- [训练数据越少，达到同一验证准确率越慢](results/2-learning-time-curves.md) — §3.1.1 · Learning time curves
- [运算结构与泛化](results/3-variety-of-operations.md) — §3.2 · Grokking on a variety of problems
- [优化器与正则化消融](results/4-ablations-and-tricks.md) — §3.3 · Ablations and tricks
- [输出层权重的 t-SNE 可视化](results/5-embedding-visualization.md) — §3.4 · Qualitative visualization of embeddings
- [验证损失的二次下降](results/6-validation-loss.md) — 附录 A.2 · Additional figures
- [记住随机标签的同时能否泛化？](results/7-memorizing-outliers.md) — 附录 A.4 · Generalization with memorizing several outliers
- [验证准确率与损失地形尖锐度](results/8-sharpness-and-generalization.md) — 附录 A.5 · Generalization measures

### 表格（`tables/`）

- [测试的二元运算](tables/table-1-binary-operations.md) — 附录 A.1 · 中文导读汇总
- [模型和训练超参数](tables/table-2-training-configuration.md) — 附录 A.1 · 中文导读汇总

### 图（`figures/`）

- [图 1 · 模除法、学习时间与运算表](figures/figure-1-delayed-generalization.md) — §1、§3.1
- [图 2 · 优化设置与运算种类](figures/figure-2-ablations-and-operations.md) — §3.2–3.3
- [图 3 · 输出层权重的 t-SNE](figures/figure-3-output-weight-projections.md) — §3.4
- [图 4 · 模除法训练和验证损失](figures/figure-4-modular-division-loss.md) — 附录 A.2
- [图 5 · 由抽象符号组成的运算表](figures/figure-5-operation-symbols.md) — 附录 A.2
- [图 6 · 随机标签对数据效率的影响](figures/figure-6-label-outliers.md) — 附录 A.4
- [图 7 · 验证准确率与尖锐度](figures/figure-7-accuracy-and-sharpness.md) — 附录 A.5

### 讨论（`discussion/`）

- [更多计算能否弥补数据不足？](discussion/discussion.md) — §4 · Discussion

### 参考文献（`references/`）

- [原论文参考文献](references/references.md) — 参考文献

### 归档与元数据

- [论文元数据 `_meta.md`](_meta.md)
- [中文导读和附录归档 `full.md`](full.md)

---

⬆️ **上一级索引**：[../INDEX.MD](../INDEX.MD)
