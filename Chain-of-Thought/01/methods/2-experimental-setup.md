> [返回论文索引](../INDEX.MD) · §3.1、§4–5

# 实验设置

| 任务族 | 任务 | 示例来源与划分 |
|---|---|---|
| 算术 | GSM8K、SVAMP、ASDiv、AQuA、MAWPS | 除 AQuA 外复用同一组 8 个人工编写示例；AQuA 为多选题，使用训练集的 4 个示例与解法。 |
| 常识 | CSQA、StrategyQA、Date Understanding、Sports Understanding、SayCan | CSQA、StrategyQA 从训练集取题并补写步骤；两项 BIG-bench 任务取评估集前 10 题作示例，剩余题作评估；SayCan 用 6 个训练示例。 |
| 符号 | 末字母拼接、硬币翻转状态追踪 | 示例为 2 步；评估含同分布 2 步，以及 3、4 步长度外推。 |

模型包括 LaMDA（正文最小规模写作 422M，结果表写作 420M）、GPT-3 API 的四种规模、PaLM 8B/62B/540B，以及 UL2 20B 和 Codex。GPT-3 参数量是论文对 API 型号的估计。使用贪心解码；LaMDA 对 5 个随机示例顺序取平均，其他模型主实验只报告一个顺序。常识和符号实验的完整模型覆盖见相应结果表。

[算术评估集的样本量与示例题](../tables/table-8-arithmetic-datasets.md)

[完整提示的位置](../appendix/2-exemplars-and-prompts.md)
