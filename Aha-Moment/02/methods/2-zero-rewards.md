> [论文索引](../INDEX.MD) · DeepSeek-R1-Zero / Reward Design

# R1-Zero 的规则奖励

以 DeepSeek-V3-Base 为初始策略，不先做 SFT。准确性奖励来自任务验证器，如固定数学答案的匹配、编程题测试用例和选择题选项匹配；格式奖励要求以指定标签区分推理和答案。两项等权：$R_{\rm rule}=R_{\rm acc}+R_{\rm format}$。[训练模板](../tables/table-1-zero-template.md)只给结构，不规定具体解法。

R1-Zero 避免在推理训练中用神经奖励模型作为主要奖励，因为作者观察到该类奖励可在训练中上升而实际任务表现下降。参见[奖励投机实验](../figures/supp-reward-hacking.md)和 [Zero 训练表现](../results/1-zero-evolution.md)。
