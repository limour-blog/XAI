# DeepSeek-R1 — 元数据

> [论文索引](INDEX.MD)

```meta
paper_id: 02
status: done
title: DeepSeek-R1: Incentivizing Reasoning Capability in LLMs via Reinforcement Learning
lang: en
journal: arXiv
year: 2025
doi:
authors_short: DeepSeek-AI
keywords: Large Language Model; Reasoning; Reinforcement Learning
one_liner: R1-Zero 不经初始 SFT，采用可验证奖励训练后，AIME 2024 pass@1 从 15.6% 提升到 77.9%。
```

## Abstract

DeepSeek-R1-Zero uses outcome and format rewards with GRPO on DeepSeek-V3-Base, without a preliminary supervised fine-tuning stage. Its trajectories become longer and contain more reflection and verification markers during training. DeepSeek-R1 adds cold-start and rejection-sampled supervised training plus mixed-reward RL for both reasoning and general instruction following. Distillation transfers a portion of this performance to smaller Qwen and Llama models.
