> [论文索引](../INDEX.MD) · Supplementary / Background

# DeepSeek-V3、常规后训练与 PPO 对照

DeepSeek-V3 为 MoE（671B 总参数、37B 每 token 激活），预训练使用 14.8T token；用 MLA、无辅助损失负载均衡与多 token 预测。原文称基座主要在中英网页和电子书上训练，未刻意加入 OpenAI 生成的合成数据，但公开网页可能含模型生成答案。因此“跳过 SFT”不是“从未接触推理文本”。V3 指指令模型，V3-Base 是 R1 与 R1-Zero 的共同基座。

常规 SFT→RL 先从样例学习任务与格式，再用奖励优化。R1-Zero 则跳过起步 SFT，先用可验证答案鼓励探索，再把有用轨迹用于后续 SFT 或蒸馏。[GRPO](../methods/1-grpo.md)与 PPO 的重点区别在于用组内奖励估计优势，不另训价值模型；在损失中加入 KL 估计，而不是把逐 token KL 作为稠密奖励。[示意图](../figures/supp-grpo.md)

在 DeepSeek-Coder-V2-Lite（16B MoE/2.4B 激活）的 MATH 对照中，PPO 的 GAE $\lambda=0.95$ 时弱于 GRPO，调成 1.0 后接近。[实验图](../figures/supp-ppo-vs-grpo.md)支持作者关于该设置下资源开销和调参负担的比较，不证明 GRPO 在所有设置下都更准。
