# Grokking：小型算法任务上的延迟泛化

> **渐进式披露 · Level 0（顶层入口）**
> 本文件是整个论文集的第一披露层：以**一句话核心结论**概览每篇论文，并链接到各论文的子索引（`NN/INDEX.MD`）获取完整摘要与细节。
> 阅读路径：本文件 → 论文 `INDEX.MD` → 章节文件（results / methods / tables …）→ 具体表格/图片/参考文献。

**Grokking（延迟泛化）**：模型很早就能答对几乎所有训练题，但直到继续训练很久，才在未见过的题目上表现良好。区别不只是准确率突然提高，而是提高之前训练集和留出集的表现已经分离了一段时间。

建议先读 01 看现象和数据量的影响，再读 02 看如何用频率消融追踪模型内部的变化。第二篇的傅里叶乘法解释的是特定模加法模型，不是第一篇所有任务的统一算法。

## 状态图例（Legend）

- ✅ 已完成渐进式重构（含 `INDEX.MD` 与 `_meta.md`）
- ⏳ 待处理（仅有 `full.md` 原文）

## 论文清单（Papers 01–02）

| # | 状态 | 标题 | 核心结论 | 入口 |
|---|---|---|---|---|
| 01 | ✅ 已重构 | Grokking: Generalization Beyond Overfitting on Small Algorithmic Datasets | 模 97 除法中，训练准确率不到 1,000 步已接近满分，验证准确率接近 1,000,000 步才达到类似水平。 | [01/INDEX.MD](01/INDEX.MD) |
| 02 | ✅ 已重构 | Progress measures for grokking via mechanistic interpretability | 模 113 加法中，5 个关键频率构成的泛化电路在约 10,000 个 epoch 的测试准确率跃升前已逐步形成。 | [02/INDEX.MD](02/INDEX.MD) |

---

## 渐进式披露结构说明（Structure convention）

每篇论文（完成后）遵循统一结构：

```
NN/
├── INDEX.MD          # Level 1: title + abstract + key findings + full navigation
├── full.md           # original full text (archive, untouched)
├── _meta.md          # machine-readable manifest (title/abstract/keywords)
├── images/           # original images
├── front-matter/     # editorial info, authors/affiliations, keywords
├── introduction/     # introduction
├── methods/          # methods (one file per subsection)
├── results/          # results (one file per result)
├── tables/           # tables (one file per table)
├── figures/          # figures + captions (one file per figure)
├── discussion/       # discussion, limitations, conclusions
├── references/       # references
└── back-matter/      # data/ethics/contributions/funding/COI/AI/publisher/supplementary
```
