> [返回论文索引](../INDEX.MD) · §4

# 常识推理

五个任务覆盖事实性常识、多跳判断、日期计算、体育表述合理性和离散机器人动作选择。PaLM 540B 在 Sports 上从 80.5% 升至 95.4%，论文引用的体育爱好者基线为 84%；SayCan 从 80.8% 至 91.7%。CSQA 仅从 78.1% 到 79.9%，GPT-3 175B 在 CSQA 和 StrategyQA 反而退步。

**源内数字差异：** StrategyQA 的 PaLM 540B CoT 在 §4 正文写作 75.6%（比较先前最好 69.4%），而图及附录模型表均写作 77.8%。[分模型表](../tables/table-4-commonsense.md)沿用表值，不把两种数字混为一个。

[图 7](../figures/figure-7-commonsense.md) · [消融与鲁棒性](../tables/table-7-commonsense-symbolic-ablation.md)
