> [论文索引](../INDEX.MD) · 附录 B.1

# Zero-shot ToT：GSM8K 与 StrategyQA

每题零样本采样 5 种策略，从中投票选一；随后按所选策略采样 5 个答案再投票。GSM8K 在测试划分、StrategyQA 在验证划分各随机抽取 100 题。提示要求在最后以 “the answer is n” 或 “the answer is yes/no” 输出。与 CoT 相比准确率分别增加 4 和 1 个百分点；论文指出 StrategyQA 的主要瓶颈可能是外部知识。参见[结果表](../tables/table-4-new-tasks.md)。
