> [论文索引](../INDEX.MD) · Supplementary / DeepSeek-R1 Distillation

# 小模型蒸馏与直接 RL 对照

使用约 80 万条样本对 Qwen、Llama 检查点仅做 SFT，不叠加 RL。[蒸馏配置](../tables/supp-distill-config.md)列出 1.5B–70B 的初始模型和学习率；[结果](../tables/supp-distill-eval.md)中 Qwen 1.5B 的 AIME pass@1 为 28.9、MATH 为 83.9，高于表中 GPT-4o 与 Claude 3.5 的数学成绩，但 GPQA 与 LiveCodeBench 仍落后。

[32B 对照](../tables/supp-distill-vs-rl.md)：Qwen2.5-32B-Base 直接做 10K 以上更新得到 Qwen2.5-32B-Zero，与 QwQ-32B-Preview 接近；同系列蒸馏模型 AIME 2024 pass@1 72.6 对 47.0、LiveCodeBench 57.2 对 40.2。这个结论针对比较的基座、数据和预算，不代表直接 RL 普遍无效。

论文另用 o1 发布前已公开的 Qwen2-Math-7B 基座做约 10,000 步 RL。[7B 表](../tables/supp-qwen-zero.md)中，Zero 在 AIME 2024/2025 达 22.3%/18.1%，高于其指令微调版本的 7.9%/4.6%。较早发布可排除基座见过公开后的 o1 轨迹，不能据此断言基座未接触任何推理文本。
