> [论文索引](../INDEX.MD) · Supplementary / More Analysis / An Analysis on CoT Length

# 随难度变化的 CoT 长度与多样采样

在 366 道竞赛题上，R1 pass@1 61.8%，平均 8,793 个 thinking token；GPT-4o-0513 为 24.7%，平均 711 个输出 token。两个 token 口径不同。[曲线](../figures/supp-test-time-scaling.md)按 pass@1 表示题目难度，统计正确作答中的思考 token；较容易的题少于 7,000，最难区域超过 18,000。它描述相关关系，不证明人为延长任一条链都会增加成功率。

同一题独立采样也有价值：在 AIME 2024，R1 pass@1 为 79.8%，pass@64 为 90.0%，多数投票达到 86.7%。与此相比，GPT-4o-0513 64 路投票只有 13.4%（pass@1 为 9.3%）。单条长链可能陷于错误路径，多样采样可以作为补充。
