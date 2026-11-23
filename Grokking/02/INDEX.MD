# Progress measures for grokking via mechanistic interpretability

> **论文 02 · 渐进式披露 Level 1**
> 本页索引中文导读和附录。原导读与附录合并归档于 [`full.md`](full.md)；英文论文版本见[来源与版本](front-matter/editorial.md)。

## 速览（At a Glance）

| 项目 | 内容 |
| --- | --- |
| 研究类型 | 机制逆向分析与控制实验 |
| 研究模型 | 模 113 加法的单层 Transformer |
| 实验设置 | 30% 输入对训练；全批量 AdamW，权重衰减系数 1 |
| 主要指标 | 训练和测试损失、准确率、限制损失与排除损失 |
| 核心发现 | 五个关键频率构成的电路在准确率跃升前已持续改善 |
| 来源 | ICLR 2023 · [arXiv:2301.05217v3](https://arxiv.org/abs/2301.05217v3) |

## 摘要（Abstract）

**背景：** 测试准确率可以突然上升，单看原始学习曲线难以判断这之前发生了什么。

**方法：** 在模 113 加法上训练单层 Transformer，通过分解权重、分析激活、进行傅里叶消融，逆向分析模型使用的算法，再从该机制构造进度指标。

**结果：** 主模型在五个关键频率上编码输入并组合旋转。限制损失和排除损失在原始测试曲线约 10,000 个 epoch 的跃升之前就已显著变化，把训练过程区分为记忆、电路形成和清理。

**结论：** 在这组实验中，准确率跃升是泛化电路逐渐增强、记忆成分随后减弱的结果。进度指标可以回看这一变化，但还不能预测新任务的跃升时间。

## 核心结论（Key Findings）

- 五个关键频率 $k\in\{14,35,41,42,52\}$ 对应模型的傅里叶乘法电路。
- 433 / 512 个 MLP 神经元，其激活超过 85% 的方差可由单频二次多项式解释。
- 隔离泛化信号后，限制损失早于原始测试损失下降；排除损失上升表明其余成分越来越难独立拟合训练集。

## 关键词（Keywords）

[延迟泛化 · 机制可解释性 · 模加法 · 傅里叶乘法 · 进度指标](front-matter/keywords.md)

## 目录导航（Level 2 → Level 3）

### 前置信息（`front-matter/`）

- [来源与版本](front-matter/editorial.md) — 论文信息
- [作者与机构](front-matter/authors-affiliations.md) — 论文信息
- [关键词](front-matter/keywords.md) — 中文导读索引词

### 引言（`introduction/`）

- [怎样看见准确率跃升之前的学习进展？](introduction/introduction.md) — §1 · Introduction
- [相关工作：进度指标与训练动态](introduction/related-work.md) — §2 · Related work

### 方法（`methods/`）

- [模 113 加法的主实验设置](methods/1-experimental-setup.md) — §3 · Setup and background
- [用旋转计算模加法](methods/2-fourier-multiplication.md) — §3.1 · The Fourier multiplication algorithm
- [如何计算限制损失和排除损失](methods/3-fourier-progress-measures.md) — §5.1 · Progress measures
- [单层 Transformer 的残差流与输出公式](methods/4-transformer-structure.md) — 附录 A · Mathematical structure of the Transformer
- [多个频率如何拉开答案分差？](methods/5-constructive-interference.md) — 附录 B · Why use constructive interference?

### 结果（`results/`）

- [主实验的训练与测试曲线](results/1-baseline-grokking.md) — §3 · Setup and background
- [嵌入、激活和 logits 的周期性](results/2-periodicity.md) — §4.1 · Suggestive evidence: surprising periodicity
- [读出模型权重里的三角恒等式](results/3-composing-model-weights.md) — §4.2 · Mechanistic evidence: composing model weights
- [用单频二次多项式拟合神经元](results/4-fitting-neuron-activations.md) — §4.3 · Zooming in: approximating neurons with sines and cosines
- [频率和读出方向的消融](results/5-frequency-ablations.md) — §4.4 · Correctness checks: ablations
- [记忆、电路形成与清理](results/6-training-phases.md) — §5.2 · Phases of grokking
- [权重衰减和训练数据量的作用](results/7-weight-decay.md) — §5.3 · Grokking and weight decay
- [哪些计算路径可以省略？](results/8-model-simplifications.md) — 附录 A.1 · Empirical model simplifications
- [四个注意力头的角色](results/9-attention-heads.md) — 附录 C.1 · Further analysis of the specific training run
- [种子、样本占比、深度和模数的对照](results/10-other-training-runs.md) — 附录 C.2 · Additional results from different runs
- [权重衰减、dropout 与 L1 惩罚的对照](results/11-regularization-controls.md) — 附录 D.1 · Regularization and limited data
- [Slingshot 不是延迟泛化的必要步骤](results/12-slingshot.md) — 附录 D.2 · The slingshot mechanism
- [三个算法任务的有限数据对照](results/13-other-algorithmic-tasks.md) — 附录 D.3 · Additional evidence from other algorithmic tasks

### 表格（`tables/`）

- [表 1 · MLP 激活在关键读出方向的傅里叶分量](tables/table-1-mlp-fourier-projections.md) — §4.2 · 原论文表 1
- [表 2 · 注意力头的正弦与余弦拟合](tables/table-2-attention-head-fits.md) — 附录 C.1 · 原论文表 2
- [主实验的数据、架构和超参数](tables/table-3-main-run.md) — §3 · 中文导读汇总
- [进度指标的定义和读法](tables/table-4-progress-measures.md) — §5.1 · 中文导读汇总
- [记忆、电路形成与清理的观测对照](tables/table-5-training-phases.md) — §5.2 · 中文导读汇总
- [不同实验条件下的泛化](tables/table-6-cross-run-comparisons.md) — 附录 C.2 · 中文导读汇总
- [每步重采样与固定数据的对照](tables/table-7-finite-data-tasks.md) — 附录 D.3 · 中文导读汇总

### 图（`figures/`）

图号沿用原论文；这里只收录导读和附录用到的图。

- [图 1 · 模加法的傅里叶乘法电路](figures/figure-1-fourier-multiplication-circuit.md) — §1、§3.1
- [图 2 · 主实验的准确率和损失](figures/figure-2-training-and-test-curves.md) — §3
- [图 3 · 嵌入与读出权重的频域分量](figures/figure-3-embedding-fourier-components.md) — §4.1
- [图 4 · 注意力分数、MLP 激活与 logits 的周期性](figures/figure-4-periodicity-of-activations.md) — §4.1
- [图 5 · 神经元的频率拟合及对 logits 的贡献](figures/figure-5-neuron-frequency-fits.md) — §4.3
- [图 6 · 消融各频率后的损失](figures/figure-6-frequency-ablation.md) — §4.4
- [图 7 · 进度指标与训练阶段](figures/figure-7-training-progress-measures.md) — §5
- [图 8 · 叠加余弦以增强正确答案的峰值](figures/figure-8-constructive-interference.md) — 附录 B
- [图 9 · 四个注意力头的周期性模式](figures/figure-9-attention-patterns.md) — 附录 C.1
- [图 12 · 其他 MLP 神经元的周期性激活](figures/figure-12-additional-neuron-activations.md) — 附录 C.1
- [图 13 · 只保留关键频率后的准确率](figures/figure-13-restricted-accuracy.md) — 附录 C.1
- [图 14 · 余弦项系数随训练的变化](figures/figure-14-cosine-coefficients.md) — 附录 C.1
- [图 15 · 逐一排除关键频率的准确率与损失](figures/figure-15-excluding-key-frequencies.md) — 附录 C.1
- [图 21 · 训练数据比例与收敛步数](figures/figure-21-steps-to-convergence.md) — 附录 C.2
- [图 23 · 两层模型的排除损失](figures/figure-23-two-layer-excluded-loss.md) — 附录 C.2
- [图 24 · 模 53 加法曲线](figures/figure-24-mod-53-loss.md) — 附录 C.2
- [图 25 · 模 401 加法曲线](figures/figure-25-mod-401-loss.md) — 附录 C.2
- [图 26 · 去掉权重衰减的对照](figures/figure-26-no-weight-decay.md) — 附录 D.1
- [图 27 · 两种权重衰减强度的对照](figures/figure-27-weight-decay-strength.md) — 附录 D.1
- [图 29 · 五位数加法：每步重采样](figures/figure-29-five-digit-addition-resampled.md) — 附录 D.3
- [图 30 · 五位数加法：固定数据](figures/figure-30-five-digit-addition-fixed-data.md) — 附录 D.3
- [图 31 · 重复子序列：每步重采样](figures/figure-31-repeated-subsequences-resampled.md) — 附录 D.3
- [图 32 · 重复子序列：固定数据](figures/figure-32-repeated-subsequences-fixed-data.md) — 附录 D.3
- [图 33 · Skip trigram：每步重采样](figures/figure-33-skip-trigram-resampled.md) — 附录 D.3
- [图 34 · Skip trigram：固定数据](figures/figure-34-skip-trigram-fixed-data.md) — 附录 D.3

### 讨论（`discussion/`）

- [记忆、泛化和相变的机制假说](discussion/discussion.md) — 附录 E · Further speculations on grokking
- [能否推广到大模型并预测跃升时间？](discussion/limitations.md) — §6、附录 F
- [从逆向分析到训练进度指标](discussion/conclusions.md) — §6 · Conclusion and discussion

### 参考文献（`references/`）

- [原论文参考文献](references/references.md) — 参考文献

### 复现与附录（`back-matter/`）

- [复现代码与检查点](back-matter/reproducibility.md) — Reproducibility Statement
- [作者贡献](back-matter/author-contributions.md) — Author Contributions
- [原文致谢](back-matter/acknowledgments.md) — Acknowledgments

### 归档与元数据

- [论文元数据 `_meta.md`](_meta.md)
- [中文导读和附录归档 `full.md`](full.md)

---

⬆️ **上一级索引**：[../INDEX.MD](../INDEX.MD)
