# Scaling Monosemanticity: Extracting Interpretable Features from Claude 3 Sonnet

> ⬆️ [Superposition 总索引](../INDEX.MD) · **论文 02（Level 1）**

| 项目 | 内容 |
| --- | --- |
| 作者 | Adly Templeton et al.（Anthropic） |
| 出处 | *Transformer Circuits Thread*，2024-05-21；[arXiv:2605.29358v1](https://arxiv.org/abs/2605.29358v1) |
| 对象 | 经过微调的 Claude 3.0 Sonnet；中间层残差流 |
| 方法 | 稀疏字典学习、自动解释、特征干预、归因与消融 |
| 训练规模 | 1,048,576 / 4,194,304 / 33,554,432 个字典槽；各模型平均每 token 少于 300 个活跃特征，解释至少 65% 的激活方差 |
| 来源 | [原始 TeX](../../TeX/Superposition/arXiv-2605.29358v1/main.tex) · [作者 HTML 版](https://transformer-circuits.pub/2024/scaling-monosemanticity/index.html) · [元数据](_meta.md) |

本目录是根据 TeX 源稿直接编写的分章节阅读版，保留原摘要、关键公式、实验数字和源稿引用的静态图。逐 token 着色示例、完整引用和详细贡献名单见原稿。

## Abstract

We demonstrate that sparse autoencoders can extract interpretable features from Claude 3 Sonnet, a production-scale language model, addressing the open question of whether dictionary learning methods scale beyond small transformers. We trained sparse autoencoders with up to 34 million features on the model's middle layer residual stream, using scaling laws to guide hyperparameter selection. The resulting features are multilingual and multimodal (generalizing to images despite text-only training), respond to both concrete instances and abstract discussions of concepts, and can be used to steer model behavior in ways consistent with their interpretations. We find features corresponding to famous entities and locations, as well as more abstract concepts like sarcasm or errors in code. We also identify features relevant to ways in which language models might cause harm—including features representing deception, power-seeking, sycophancy, and bias—and show that these causally influence model outputs when manipulated. Additionally, we conduct analyses of feature interpretability, geometry, and computational function. However, significant limitations remain: our suite of features is incomplete, and we lack rigorous methods for evaluating whether our features faithfully capture model computations.

## 核心结论

- 在测试范围内，最优训练损失随算力近似按幂律下降。损失是训练代理指标，不等同于可解释性或机制保真度。
- 金门大桥等示例在多语言文本和部分图像中触发相同方向。特征干预能改变某些输出，但强干预不等同于自然激活。
- 更大的字典更容易找到罕见概念的专用特征，但覆盖仍不完整：34M 字典只找到约 60% 的伦敦行政区对应特征。
- 在两项案例中，特征归因与实测消融效应的相关系数约为 0.81，而原始激活与消融效应的相关系数为 0.12。

## 章节导航

### 背景、方法与前置信息
- [作者与发表信息](front-matter/authors-affiliations.md)
- [引言与研究动机](introduction/introduction.md)
- [§1.1 稀疏自编码器：编码、解码与损失](methods/1-sparse-autoencoders.md)
- [§5 特征搜索：单提示、对照、几何和归因](methods/3-feature-search.md)
- [附录：样本选择、特征干预、少样本探针对比](methods/2-dataset-and-steering.md)
- [§8 相关工作](introduction/related-work.md)

### 实验结果
- [§1.2–1.3 SAE 实验与缩放规律](results/1-scaling-laws.md)
- [§2.1 四个示例：特异性与敏感性](results/2-specificity.md)；[对行为的影响](results/3-behavior.md)
- [§2.2 复杂代码特征：错误与加法函数](results/4-sophisticated-features.md)
- [§2.3 SAE 特征与神经元对比](results/5-features-vs-neurons.md)
- [§3.1 特征邻域及特征拆分](results/6-neighborhoods.md)
- [§3.2 覆盖率与概念频率](results/7-completeness.md)
- [§3.3 人物、国家、代码和列表位置](results/8-feature-categories.md)
- [§4 计算中间变量：情绪推断与多步推断](results/9-computational-intermediates.md)
- [§6 安全相关特征研究](results/11-safety-relevant-features.md)
- [附录：消融与归因对比](results/12-ablation-and-attribution.md)

### 图表

图号沿用源稿资源编号 `fig:gdoc_*`。源稿实际引用 002–044；图内原有文字保留，图页提供文字导读。

| 主题 | 图页 |
| --- | --- |
| 引言与缩放规律 | [002](figures/figure-002.md) · [003](figures/figure-003.md) · [004](figures/figure-004.md) |
| 特异性与行为 | [005](figures/figure-005.md) · [006](figures/figure-006.md) · [007](figures/figure-007.md) · [008](figures/figure-008.md) · [009](figures/figure-009.md) |
| 代码错误 | [010](figures/figure-010.md) · [011](figures/figure-011.md) · [012](figures/figure-012.md) · [013](figures/figure-013.md) · [014](figures/figure-014.md) · [015](figures/figure-015.md) · [016](figures/figure-016.md) · [017](figures/figure-017.md) |
| 加法函数与神经元对照 | [018](figures/figure-018.md) · [019](figures/figure-019.md) · [020](figures/figure-020.md) · [021](figures/figure-021.md) · [022](figures/figure-022.md) |
| 邻域、覆盖率与类别 | [023](figures/figure-023.md) · [024](figures/figure-024.md) · [025](figures/figure-025.md) · [026](figures/figure-026.md) · [027](figures/figure-027.md) · [028](figures/figure-028.md) · [029](figures/figure-029.md) · [030](figures/figure-030.md) |
| 计算中间变量 | [031](figures/figure-031.md) · [032](figures/figure-032.md) · [033](figures/figure-033.md) · [034](figures/figure-034.md) |
| 安全相关特征 | [035](figures/figure-035.md) · [036](figures/figure-036.md) · [037](figures/figure-037.md) · [038](figures/figure-038.md) · [039](figures/figure-039.md) · [040](figures/figure-040.md) · [041](figures/figure-041.md) · [042](figures/figure-042.md) · [043](figures/figure-043.md) |
| 消融与归因验证 | [044](figures/figure-044.md) |

- [附录表：安全相关特征目录](tables/table-1-safety-feature-catalog.md)

### 讨论与文后资料
- [§7.1–7.2 对安全的含义和分布外泛化](discussion/discussion.md)
- [§7.3 局限、挑战和开放问题](discussion/limitations.md)
- [参考文献与外部资源](references/references.md)
- [附录：作者贡献、致谢与引用信息](back-matter/publication-notes.md)
