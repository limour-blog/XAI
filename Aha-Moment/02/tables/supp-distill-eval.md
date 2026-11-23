> [论文索引](../INDEX.MD) · [蒸馏分析](../results/11-distillation.md)

# Reasoning benchmarks for distilled models

原表 `tab:distill`；除 AIME cons@64 和 Codeforces rating 外，指标为 pass@1。粗体沿用原表（t-test，$p<0.01$）。

| 模型 | AIME 2024 pass@1 | AIME 2024 cons@64 | MATH | GPQA Diamond | LiveCodeBench | Codeforces rating |
|---|---:|---:|---:|---:|---:|---:|
| GPT-4o-0513 | 9.3 | 13.4 | 74.6 | 49.9 | 32.9 | 759 |
| Claude-3.5-Sonnet-1022 | 16.0 | 26.7 | 78.3 | 65.0 | 38.9 | 717 |
| R1-Distill-Qwen-1.5B | 28.9 | 52.7 | 83.9 | 33.8 | 16.9 | 954 |
| R1-Distill-Qwen-7B | 55.5 | 83.3 | 92.8 | 49.1 | 37.6 | 1189 |
| R1-Distill-Qwen-14B | 69.7 | 80.0 | 93.9 | 59.1 | 53.1 | 1481 |
| R1-Distill-Qwen-32B | **72.6** | 83.3 | 94.3 | 62.1 | 57.2 | 1691 |
| R1-Distill-Llama-8B | 50.4 | 80.0 | 89.1 | 49.0 | 39.6 | 1205 |
| R1-Distill-Llama-70B | 70.0 | **86.7** | **94.5** | **65.2** | **57.5** | **1633** |
