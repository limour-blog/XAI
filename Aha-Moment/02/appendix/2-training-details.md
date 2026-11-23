> [论文索引](../INDEX.MD) · Supplementary / Training Details

# 基础设施、数据与训练细节

**系统。** [RL 框架](../figures/supp-rl-infrastructure.md)分为 rollout、模型推断、规则奖励、参数更新四模块。推断使用 vLLM、专家并行、热点专家冗余和多 token 预测的自推测解码；规则评估异步进行。训练模块先按长度分组，再用 Best-Fit 装箱减少填充，配合 DualPipe 流水并行；阶段之间卸载不用的模型以回收显存。

**RL 数据。** 涵盖数学、代码、STEM 和逻辑，另有有用性、无害性方向的一般数据，语言为中英。[原表](../tables/supp-rl-data.md)列出各类数量和输出类型；代码项的表中数量 17K，正文另列 8K 修复题；一般项正文在 66K 有用性问题之外另列 12,000 个无害性问题。数学题避免难以机械核验的证明，代码题通过测试用例验证。

**冷启动和 SFT。** 以较高温度从 R1-Zero 生成候选，筛去错误答案、重复或混合语言轨迹。人工改写、模型扩展并二次核验以获得更易读的长链；对于简单任务，数据也示范短输出。Dev2 的拒绝采样产生约 600K 推理样本，另加约 200K 非推理样本；[明细](../tables/supp-sft-data.md)为 804,745，平均 1.0 轮、5,355.3 token。主要是单轮，限制多轮能力。[提示与样例](3-prompts-and-listings.md)

**超参数。** 冷启动与第二次 SFT 均为 2–3 epochs，上下文 32,768，batch 128，余弦学习率 $5\times10^{-5}\to5\times10^{-6}$。蒸馏同样 2–3 epochs，batch 64，余弦退火至[对应初始值](../tables/supp-distill-config.md)的十分之一。Qwen 32B 的直接 RL 用学习率 $2\times10^{-6}$、KL 0.001、温度 1，每题采 16 个、最长 32,768 token。

**成本和消融。** [成本表](../tables/supp-training-cost.md)报告 147K H800 GPU 小时，按每 GPU 小时 2 美元计约 29.4 万美元，包括 R1-Zero、SFT 数据生成与 R1 训练，不是整项研究总成本。[奖励投机](../figures/supp-reward-hacking.md)显示有用性奖励上升而 Codeforces 表现下降；[语言一致性实验](../figures/supp-language-consistency.md)显示可稳定目标语言使用，数学相近、代码稍降。
