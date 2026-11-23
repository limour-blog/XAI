> [论文索引](../INDEX.MD) · 正文 R1-Zero / Incentivize Reasoning Capability；附录 Self-Evolution

# R1-Zero 的推理行为随 RL 训练变化

[训练曲线](../figures/figure-1-zero-training.md)中 AIME 2024 pass@1 从 15.6% 到 77.9%，自洽投票达 86.7%；训练文本的平均生成长度同时增加。[数学难度曲线](../figures/supp-math-difficulty.md)中，MATH 1–3 级较早到约 0.90–0.95，4 级约 0.78→0.95，5 级约 0.55→0.90；各级题量和类别分布不平衡，不能只按排序推断因果。

作者请三名专家选反思标记词，包括 “wait”、“verify”、“mistake”、“check”。[词频图](../figures/supp-reflection.md)显示这些词的计数比训练初期增加约 5–7 倍，“wait” 在 4,000–7,000 步偶现，8,000 步后明显增多。[Aha Moment 样例](../tables/table-2-aha-moment.md)展示一条重新检查根式方程的中途轨迹。单条轨迹和词频是行为观察；词数会受输出总体变长影响，不能把标记词本身当作正确反思的充分证据。
