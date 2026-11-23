> [论文索引](../INDEX.MD) · Supplementary / DeepSeek-R1 Safety Report

# 模型与服务层安全评估

论文区分基于模型本身的安全表现和官方服务附加风控。官方流程先筛选潜在风险对话，再用 DeepSeek-V3 作风险复核。不同厂商的线上结果可能同时包含模型和服务层的影响。

| 评估 | 口径与结果 |
|---|---|
| [六个公开基准](../tables/supp-safety-eval.md) | DNA、HarmBench 由论文复现，其余来自第三方 HELM；R1 平均安全分 95.0，关闭风控的表列值 85.9。HarmBench 是差距较明显的一项。 |
| [内部分类基准](../tables/supp-safety-taxonomy.md) | [4 类 28 子类](../figures/supp-safety-taxonomy.md)，中英文共 1,120 题。区分安全回答、不安全回答、拒绝。启用风控后 R1 不安全率 25.2%→8.5%，拒绝率 5.6%→27.3%。 |
| [多语种基准](../figures/supp-multilingual-safety.md) | 50 种语言 9,330 题，安全/拒绝/不安全分别计 5/4/0 分。R1 风控前后为 74.2% 和 85.9%。 |
| [对抗性鲁棒性](../tables/supp-safety-robustness.md) | 对抗测试下无风控 R1 的不安全率为 85.9%，加风控后为 4.3%，对应拒绝率 87.3%。 |

这些结果衡量特定样本、模型版本和打分协议下的表现。降低不安全率可能同时提高拒绝率；安全、适当作答与机械拒绝需要分别报告。
