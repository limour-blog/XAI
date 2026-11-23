# Aha Moment：显式搜索与强化学习中的推理行为

> 渐进式披露 · Level 0

| # | 论文 | 一句话结论 | 入口 |
|---|---|---|---|
| 01 | Tree of Thoughts: Deliberate Problem Solving with Large Language Models | 不改 GPT-4 权重，在推理时搜索中间步骤，将 24 点成功率从 CoT 的 4% 提升到 74%。 | [论文索引](01/INDEX.MD) |
| 02 | DeepSeek-R1: Incentivizing Reasoning Capability in LLMs via Reinforcement Learning | R1-Zero 不经初始监督微调，采用可验证奖励训练后，AIME 2024 pass@1 从 15.6% 提升到 77.9%。 | [论文索引](02/INDEX.MD) |

**阅读顺序：** 先读 01，理解外部搜索如何保留、比较和回溯多个候选步骤；再读 02，查看不显式维护搜索树的模型如何在单条输出中产生检查、重试和改换解法等行为。两篇论文的任务和评估口径不同，数字不作直接横向比较。

论文索引保留英文摘要；正文按节用中文整理，保留关键公式和数据，图页链接到源目录中的 PDF。内容直接阅读 TeX 后编写，不是逐字转录；原始文件未改动。
