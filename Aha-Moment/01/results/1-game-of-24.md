> [论文索引](../INDEX.MD) · 第 4.1 节

# Game of 24

用四个整数各一次，经基本四则运算得到 24。作者从按人类解题耗时排序的 1,362 题中选取第 901–1,000 题；最终等式必须合法且值为 24。主实验默认 GPT-4 Chat Completion，温度 0.7，运行于 2023 年 5 月 5–16 日。

IO 使用 5 个示例，CoT 为每个示例增加 3 条中间等式，两者各采样 100 次求平均。自洽对 100 个 CoT 样本做投票；迭代改写基线最多 10 次，并获得验证器给出的正误反馈。ToT 将一步定义为合并两个剩余数，提示模型提出候选并独立评价 3 次，采用宽度受限 BFS。

[结果表](../tables/table-2-game-of-24.md)中 IO / CoT / CoT-SC 分别为 7.3% / 4.0% / 9.0%，ToT 宽度 1 和 5 分别为 45% 和 74%。oracle best-of-100 CoT 为 49%，与事先没有正确性信息的多数投票不可混用。约 60% 的 CoT 样本第一步即已失败。

[生成与评价](../figures/figure-2-game-search.md) · [搜索规模和错误分析](../figures/figure-3-game-analysis.md) · [跨模型](../tables/table-5-game-models.md) · [成本](../tables/table-7-game-cost.md)
