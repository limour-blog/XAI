> [返回论文索引](../INDEX.MD) · §3

# 少样本提示任务

给预训练模型一段包含少量输入—输出示例的提示，再要求完成未见过的实例；推理时无梯度更新。见[图 1](../figures/figure-1-few-shot-example.md)和[图 2](../figures/figure-2-few-shot-flops.md)。

- **BIG-Bench（A–D，2-shot）**：改编算术含三位数加减、两位数乘法。GPT-3 在约 $2\times10^{22}$ FLOPs（13B）跃升，LaMDA 在约 $10^{23}$ FLOPs（正文写 68B）跃升。音标转写、字母重排和波斯语问答也展示类似形态，模型家族与评分各异。
- **TruthfulQA（E）**：用于检验如实作答，并针对 GPT-3 对抗式整理。GPT-3 的最大模型也未超随机；Gopher 到 280B（约 $5\times10^{23}$ FLOPs）明显超随机，原文报告跃升超过随机基线 20 个百分点。
- **Grounded mappings（F）**：从文本格子世界学习如方位等概念映射；仅最大 GPT-3 明显超过随机。
- **MMLU（G）**：涵盖 57 个学科测试；约 $10^{22}$ FLOPs 或更小的模型平均近猜测，GPT-3、Gopher、Chinchilla 扩至约 $3$–$5\times10^{23}$ FLOPs 后明显改善。
- **Word in Context（H）**：GPT-3 与 Chinchilla 的最大模型在 one-shot 设定下未超过随机；PaLM 540B 在约 $2.5\times10^{24}$ FLOPs 后超过随机。GPT-3 的 few-shot 开发集约 55%，未复现到测试服务器，不能和这里的 one-shot 直接混用。

[表 1：各案例规模](../tables/table-1-emergence-scales.md) · [附录：任务分类](../appendix/6-task-annotations.md)
