> [返回论文索引](../INDEX.MD) · 致谢、检查清单和附录 E

# 复现、数据与版本

- **复现实验**：只做提示推理；提供精确提示，用四个 GPT-3 API 型号补充被评估的非公开模型。论文指向补充 ZIP 中的 LaMDA 137B 输入、目标和预测。
- **算力**：LaMDA 137B 为 TPU v3 8×8（64 芯片 / 128 核），PaLM 540B 为 TPU v4 4×4×12（192 芯片 / 384 核）；GPT-3 使用 API。
- **数据许可**：GSM8K、SVAMP、原始 StrategyQA 为 MIT；MultiArith 和 SayCan 为 CC BY 4.0；BIG-bench 日期与体育为 Apache 2.0；AQuA 见其仓库许可证。符号任务按所述规则合成。
- **版本**：v2 加入 PaLM；v3 加入 GPT-3、新基准、相关工作、FAQ 和补充结果；v4 修正图 3 并增引文；v5 增加 Codex/UL2；v6 再修正图 3 的小错误。
- **致谢**：Jacob Devlin、Claire Cui、Andrew Dai、Ellie Pavlick 提供反馈。

[附录及检查清单原文](../../../TeX/Chain-of-Thought/arXiv-2201.11903v6/neurips_2022.tex)
