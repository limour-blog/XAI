# Chain of Thought：从提示、表达能力到推理算力

> 渐进式披露 · Level 0

| # | 论文 | 一句话结论 | 入口 |
|---|---|---|---|
| 01 | Chain-of-Thought Prompting Elicits Reasoning in Large Language Models | 8 个推理示例把 PaLM 540B 的 GSM8K 准确率从 17.9% 提升到 56.9%，无需微调。 | [论文索引](01/INDEX.MD) |
| 02 | The Expressive Power of Transformers with Chain of Thought | 在论文的统一模型中，线性步数足以识别正则语言，多项式步数在指定架构下恰好覆盖 P。 | [论文索引](02/INDEX.MD) |
| 03 | Chain of Thought Empowers Transformers to Solve Inherently Serial Problems | 常数精度、对数宽度的非统一模型可用 O(T) 步模拟 T 门布尔电路；对数步在该精度模型下仍受 AC⁰ 限制。 | [论文索引](03/INDEX.MD) |
| 04 | Scaling LLM Test-Time Compute Optimally can be More Effective than Scaling Model Parameters | 在 MATH 上按题目难度分配算力，64 次自适应修订可超过 256 次并行采样的基线。 | [论文索引](04/INDEX.MD) |

**阅读顺序：** 先读 01 看自然语言提示的实证效果；并读 02、03，比较统一的图灵机模拟与非统一的电路模拟；最后读 04，看测试时预算如何分给搜索或修订。

各论文索引包含英文摘要、关键结论及分层导航。章节、数据表和图注直接从源 TeX 阅读后编写；正文和证明采用分节整理，不是逐字全文转录。各论文附有对应版本的本地源文件入口，原始 TeX 未改动。
