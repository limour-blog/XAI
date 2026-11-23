# Transformers Learn In-Context by Gradient Descent

← [专题索引](../INDEX.MD) · [arXiv:2212.07677v2](https://arxiv.org/abs/2212.07677v2) · [ICML 2023 / PMLR](https://proceedings.mlr.press/v202/von-oswald23a.html)

根据 [LaTeX 原稿](../../TeX/In-Context-Learning/arXiv-2212.07677v2/ICML.tex) 直接编写的中文章节导读，保留命题、主要公式、实验设置和原图面板。PDF 格式的面板以链接提供。

## 摘要

作者提出：在自回归学习中，Transformer 的参数训练可看作外循环，前向传播可对上下文构造的隐式损失执行梯度更新。理论上，一层线性自注意力能够精确复现线性回归的一步梯度下降。合成回归实验中，训练所得单层模型接近所构造的权重，多层模型则可表现得像带曲率校正的 GD++。模型也能在 MLP 特征上适配线性读出以完成非线性回归，或先用一个注意力层配对输入和标签、再由下一层执行更新。实验对象是小型 Transformer 和简单回归，不是对真实语言模型内循环的直接验证。

### Abstract (original)

At present, the mechanisms of in-context learning in Transformers are not well understood and remain mostly an intuition. In this paper, we suggest that training Transformers on auto-regressive objectives is closely related to gradient-based meta-learning formulations. We start by providing a simple weight construction that shows the equivalence of data transformations induced by 1) a single linear self-attention layer and by 2) gradient-descent (GD) on a regression loss. Motivated by that construction, we show empirically that when training self-attention-only Transformers on simple regression tasks either the models learned by GD and Transformers show great similarity or, remarkably, the weights found by optimization match the construction. Thus we show how trained Transformers become mesa-optimizers i.e. learn models by gradient descent in their forward pass. This allows us, at least in the domain of regression problems, to mechanistically understand the inner workings of in-context learning in optimized Transformers. Building on this insight, we furthermore identify how Transformers surpass the performance of plain gradient descent by learning an iterative curvature correction and learn linear models on deep data representations to solve non-linear regression tasks. Finally, we discuss intriguing parallels to a mechanism identified to be crucial for in-context learning termed *induction-head* ([Olsson et al.](../arXiv-2209.11895v1/INDEX.MD)) and show how it could be understood as a specific case of in-context learning by gradient descent learning within Transformers.

## 正文

- [§1 · 研究假设与外循环／内循环](introduction/introduction.md)
- [§2 / A.1 · 线性自注意力等价于一步 GD：命题 1 与显式权重](methods/1-attention-and-gradient-descent.md)
- [§3 · 合成任务、外循环损失和对齐指标](methods/2-training-and-evaluation.md)
- [§3.1 · 单层结果：权重插值、分布外与重复执行](results/1-single-layer.md)
- [§3.2 · 多层结果：普通 GD 与 GD++](results/2-multiple-layers.md)
- [§3.3 · 正弦波回归与深层特征：命题 2](results/3-nonlinear-regression.md)
- [§4 · 从交替 token 构造回归样本：命题 3](results/4-token-copying.md)
- [§5 · 讨论与适用范围](discussion/discussion.md)

## 附录

- [A.2 · 分布外行为](appendix/2-ood.md)
- [A.3–A.4 · 权重插值与可视化](appendix/3-weight-interpolation.md)
- [A.5 · 复制层的构造](appendix/5-copy-construction.md)
- [A.6 · 重复更新的阻尼](appendix/6-dampening.md)
- [A.7 · 正弦波任务设置](appendix/7-sine-wave.md)
- [A.8 · 核回归与核平滑](appendix/8-kernels.md)
- [A.9 · Softmax 与 LayerNorm](appendix/9-softmax-layernorm.md)
- [A.10 · 曲率校正的公式与谱分析](appendix/10-curvature.md)
- [A.11 · 训练相变](appendix/11-phase-transitions.md)
- [A.12 · 超参数与固定任务集](appendix/12-experimental-details.md)

## 原图

1. [学习机制示意](figures/figure-1-hypothesis.md)
2. [一步 GD 与单层 LSA](figures/figure-2-single-layer.md)
3. [两层／五层与 GD++](figures/figure-3-multiple-layers.md)
4. [正弦波回归](figures/figure-4-sine-regression.md)
5. [复制并配对 token](figures/figure-5-copying.md)
6. [分布外测试](figures/figure-6-ood.md)
7. [十步循环](figures/figure-7-ten-layers.md)
8. [十二层四头](figures/figure-8-twelve-layers.md)
9. [权重矩阵乘积](figures/figure-9-weights.md)
10. [阻尼与重复更新](figures/figure-10-rollout.md)
11. [双头 softmax 权重](figures/figure-11-softmax-weights.md)
12. [单头与双头 softmax](figures/figure-12-softmax.md)
13. [曲率与条件数](figures/figure-13-curvature.md)
14. [LayerNorm](figures/figure-14-layernorm.md)
15. [训练相变与 grokking](figures/figure-15-phase-transitions.md)
16. [固定训练任务集](figures/figure-16-fixed-tasks.md)

## 书目信息

[作者与关键词](front-matter/authors-and-keywords.md) · [参考文献](references/references.md) · [致谢](back-matter/acknowledgments.md) · [元数据](_meta.md)
