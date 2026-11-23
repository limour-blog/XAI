> [论文索引](../INDEX.MD) · Supplementary / Evaluation / Experiment Setup

# 基准、去污染与 pass@1 估计

覆盖通用知识和事实性、长文问答、指令跟随、开放式偏好、算法竞赛、软件工程及数学。正式模型最大生成长度 32,768 token；默认温度 0.6、top-p 0.95。为降低贪心评估的波动，对同题采样多次并取正确指示变量均值估计 pass@1（AIME 与 GPQA 各 64 样本，MATH、Codeforces 各 16，LiveCodeBench 8）。**cons@64** 是对 64 个答案作多数投票，**pass@64** 则表示 64 个样本中至少有一个正确，不是同一指标。主文 Zero 训练图另用 Cons@16 标示其曲线。

开放式偏好评估遵循 AlpacaEval 2.0、Arena-Hard 协议，以 GPT-4-Turbo-1106 仅查看最终总结作成对比较，减小输出长度影响。软件工程 SWE-Bench Verified 使用 Agentless；LiveCodeBench 用 2024 年 8 月至 2025 年 1 月的题。

预训练与后训练以题面和参考答案匹配 10-gram 去重；仅在数学领域就过滤约 600 万条潜在预训练文本。后训练数学数据来自 2023 年以前的竞赛。精确字符串过滤无法识别全部改写，作者因此另报告[更新竞赛](../results/7-new-competitions.md)。

[标准基准结果](../results/3-benchmarks.md) · [评估提示样例定位](../appendix/4-evaluation-examples.md)
