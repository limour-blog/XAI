# Othello-GPT：从棋盘状态到线性情感表征

> **渐进式披露 · Level 0（顶层入口）**
> 本文件是整个论文集的第一披露层：以**一句话核心结论**概览每篇论文，并链接到各论文的子索引（`NN/INDEX.MD`）获取完整摘要与细节。
> 阅读路径：本文件 → 论文 `INDEX.MD` → 章节文件（results / methods / tables …）→ 具体表格/图片/参考文献。

这两篇论文用不同的任务区分**可以从激活读出什么**和**模型预测实际用到了什么**。先读 01：从黑白棋走子序列解码棋盘，再通过反事实棋格编辑检验因果作用。接着读 02：把同样的问题带到自然语言，用方向替换和消融研究情感，以及模型如何把情感信息汇总到逗号等位置。

索引用中文，论文摘要保留英文原文；各章根据本地 TeX 源文直接撰写英文 Markdown。连续阅读版汇编各章、图表和附录；逐字原文与完整书目可从各篇的源文链接查阅。

## 推荐阅读

只想了解黑白棋的实验，直接进入 [01 的因果干预结果](01/results/4-causal-role.md)；想比较自然语言中的证据，再读 [02 的情感方向验证](02/results/3-causal-evaluation.md)。

## 论文清单（Papers 01–02）

| # | 状态 | 标题 | 核心结论 | 入口 |
|---|---|---|---|---|
| 01 | ✅ 已重构 | Emergent world representations: Exploring a sequence model trained on a synthetic task | Othello-GPT 的棋盘状态可被探针读出（黑／白／空分类最低错误率 1.7%）；改写该状态会改变合法落子的预测。 | [01/INDEX.MD](01/INDEX.MD) |
| 02 | ✅ 已重构 | Linear Representations of Sentiment in Large Language Models | 单一残差流方向能表征情感；在筛选后的 SST 子集上，仅消融逗号位置的该方向就使准确率下降 18 个百分点。 | [02/INDEX.MD](02/INDEX.MD) |

---

## 渐进式披露结构说明（Structure convention）

两篇论文均可从单篇索引进入，也可打开 `full.md` 连续阅读。

```text
NN/
├── INDEX.MD          # 摘要、核心发现及完整导航
├── full.md           # 根据源文整理的连续阅读版
├── _meta.md          # 机器可读的论文元数据
├── images/           # 原始位图与 PDF 插图的 PNG 预览
├── front-matter/     # 作者、机构与原始 LaTeX 链接
├── introduction/    # 引言
├── methods/         # 方法
├── results/         # 分实验的结果
├── tables/          # 单独的表格页
├── figures/         # 单独的插图页、图注与相关章节
├── discussion/      # 讨论、结论及局限
├── appendix/        # 补充实验、指标与数据细节
├── references/      # 关键文献与完整书目源文件
└── back-matter/     # 论文中已有的文末声明
```
