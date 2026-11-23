> [返回论文索引](../INDEX.MD) · [少样本](../results/1-few-shot-tasks.md) · [增强策略](../results/2-augmented-prompting.md)

# 表 1 · 涌现能力与首次观测规模

[原表](../../../TeX/Emergent/arXiv-2206.07682v2/big_table.tex)。数字沿用表格口径，非必要阈值。

| 少样本任务 | 训练 FLOPs | 参数 | 模型 | 来源 |
|---|---:|---:|---|---|
| 3 位加减 | 2.3E+22 | 13B | GPT-3 | Brown et al. |
| 4–5 位加减 | 3.1E+23 | 175B | GPT-3 | Brown et al. |
| MMLU（57 主题平均） | 3.1E+23 | 175B | GPT-3 | Hendrycks et al. |
| 毒性分类 CivilComments | 1.3E+22 | 7.1B | Gopher | Rae et al. |
| TruthfulQA | 5.0E+23 | 280B | Gopher | Rae et al. |
| MMLU（26 主题） | 5.0E+23 | 280B | Gopher | Rae et al. |
| Grounded conceptual mappings | 3.1E+23 | 175B | GPT-3 | Patel & Pavlick |
| MMLU（30 主题） | 5.0E+23 | 70B | Chinchilla | Hoffmann et al. |
| WiC | 2.5E+24 | 540B | PaLM | Chowdhery et al. |
| [多个 BIG-Bench 任务](../appendix/6-task-annotations.md) | 多种 | 多种 | 多种 | BIG-Bench |

| 增强策略 | 训练 FLOPs | 参数 | 模型 | 来源 |
|---|---:|---:|---|---|
| 指令微调 | 1.3E+23 | 68B | FLAN | Wei et al. |
| Scratchpad：8 位加法微调 | 8.9E+19 | 40M | LaMDA | Nye et al. |
| 开卷事实核验 | 1.3E+22 | 7.1B | Gopher | Rae et al. |
| CoT：数学文字题 | 1.3E+23 | 68B | LaMDA | Wei et al. |
| CoT：StrategyQA | 2.9E+23 | 62B | PaLM | Chowdhery et al. |
| 可微搜索索引 | 3.3E+22 | 11B | T5 | Tay et al. |
| 自洽解码 | 1.3E+23 | 68B | LaMDA | Wang et al. |
| 在提示中利用解释 | 5.0E+23 | 280B | Gopher | Lampinen et al. |
| Least-to-most 提示 | 3.1E+23 | 175B | GPT-3 | Zhou et al. |
| 零样本 CoT | 3.1E+23 | 175B | GPT-3 | Kojima et al. |
| P(True) 校准 | 2.6E+23 | 52B | Anthropic | Kadavath et al. |
| 多语言 CoT | 2.9E+23 | 62B | PaLM | Shi et al. |
| Ask Me Anything 提示 | 1.4E+22 | 6B | EleutherAI | Arora et al. |
