> [返回论文索引](../INDEX.MD) · §3.2

# 算术推理

PaLM 540B 的 GSM8K 准确率从标准提示的 17.9% 增至 56.9%（+39.0 个百分点），超过论文引用的 55% 微调验证器基线。GPT-3 175B 从 15.6% 到 46.9%；Codex 从 19.7% 到 63.1%。PaLM 540B 在 SVAMP、MAWPS 达到 79.0%、93.3%；其标准提示在 SVAMP 上已有 69.4%，超过该论文引用的历史基线 57.4%。

较小模型在多项基准上反而退步，会生成流畅但逻辑不通的中间步骤。收益也依赖题目复杂度：PaLM 540B 的 MAWPS SingleOp 为 94.1% → 94.1%，MultiArith 则是 42.2% → 94.7%。因此约 100B 的描述是对本组模型与任务的经验概括，不是普适参数阈值。

附录还把外部计算器用于已有表达式，并通过字符串匹配传播中间结果；它不修复题意理解错误。PaLM 540B 在 GSM8K 达到 58.6%，而 ASDiv 从 73.9% 降至 72.6%。

[图 2：GSM8K](../figures/figure-2-gsm8k.md) · [图 4：算术曲线](../figures/figure-4-arithmetic.md) · [主模型和计算器](../tables/table-1-flagship-arithmetic.md) · [全模型](../tables/table-2-all-arithmetic.md) · [MAWPS 子集](../tables/table-3-mawps.md) · [错误分析](../appendix/1-faq-and-errors.md)
