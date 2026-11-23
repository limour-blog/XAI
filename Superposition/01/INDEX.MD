# Toy Models of Superposition

> ⬆️ [Superposition 总索引](../INDEX.MD) · **论文 01（Level 1）**

| 项目 | 内容 |
| --- | --- |
| 作者 | Nelson Elhage et al. |
| 出处 | Transformer Circuits Thread，2022-09-14；[arXiv:2209.10652v1](https://arxiv.org/abs/2209.10652v1) |
| 实验 | 合成稀疏特征；输出 ReLU 重建、隐藏层 ReLU 重建、绝对值计算 |
| 核心发现 | 五个特征在二维瓶颈中随稀疏度增加，由两个独占维度变为四个反向配对特征，再变为五边形。 |
| 来源 | [未经修改的全文](full.md) · [作者 HTML 版（交互图）](https://transformer-circuits.pub/2022/toy_model/index.html) · [元数据](_meta.md) |

## Abstract

Neural networks often pack many unrelated concepts into a single neuron – a puzzling phenomenon known as 'polysemanticity' which makes interpretability much more challenging. This paper provides a toy model where polysemanticity can be fully understood, arising as a result of models storing additional sparse features in "superposition." We demonstrate the existence of a phase change, a surprising connection to the geometry of uniform polytopes, and evidence of a link to adversarial examples. We also discuss potential implications for mechanistic interpretability.

## 核心结论

- 非正交方向可以承载更多稀疏特征，但会引入交叉干扰。输出 ReLU 可以截断负干扰，负偏置还能抑制部分小幅正干扰。
- 特征重要度与稀疏度共同决定特征是否被忽略、共享空间或独占维度；等重要度和等稀疏度下可形成反向对、三角形、四面体等结构。
- 有特权基底时，单义与多义神经元可以共存。绝对值实验为简单非线性计算也能在叠加中进行提供了存在性证据。

## 章节导航

下列章节按原文拆分；源 Markdown 中提取不完整的公式、图注和交互图可对照作者的 HTML 版。

### 前言与定义
- [作者与发表信息](front-matter/authors-affiliations.md)
- [引言](introduction/introduction.md)
- [定义与动机：特征、方向、特权基底](introduction/definitions-and-motivation.md)
- [相关工作](introduction/related-work.md)

### 方法
- [输出 ReLU 模型和线性基线](methods/1-relu-output.md)
- [数学分析：表示收益与干扰](methods/2-mathematical-understanding.md)
- [绝对值模型设置](methods/3-absolute-value.md)
- [附录：非线性压缩与压缩感知下界](methods/4-nonlinear-compression.md)

### 结果
1. [叠加演示](results/1-demonstrating-superposition.md)
2. [稀疏度与重要度相图](results/2-phase-change.md)
3. [均匀叠加与特征维度](results/3-uniform-geometry.md)
4. [非均匀叠加与几何变形](results/4-non-uniform-geometry.md)
5. [相关、反相关与局部近正交基底](results/5-correlations.md)
6. [学习动态](results/6-learning-dynamics.md)
7. [与对抗稳健性的关系](results/7-adversarial-robustness.md)
8. [有特权基底的叠加](results/8-privileged-basis.md)
9. [叠加中的绝对值计算](results/9-computation.md)

### 图表
- [五特征、二维瓶颈（引言示意）](figures/figure-1-five-features.md)
- [复现图 1：损失曲面](figures/replication-figure-1-loss-surfaces.md)
- [相对特征密度表](tables/table-1-relative-feature-density.md)
- 其他未编号插图和子图保留在各自章节中。

### 讨论与文后资料
- [叠加对可解释性的影响与三种研究路线](discussion/strategic-picture.md)
- [讨论与开放问题](discussion/discussion.md)
- [评论与独立复现](back-matter/comments-and-replications.md)
- [代码、致谢、贡献与引用格式](back-matter/publication-notes.md)
- [参考文献与脚注](references/references.md)
