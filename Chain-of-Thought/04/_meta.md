> [返回论文索引](INDEX.MD)

# _meta

```meta
paper_id: 04
status: done
title: Scaling LLM Test-Time Compute Optimally can be More Effective than Scaling Model Parameters
lang: en
journal: arXiv
year: 2024
doi:
authors_short: Snell et al.
keywords: test-time compute; process reward model; beam search; iterative revision; difficulty
one_liner: 在 MATH 上按题目难度分配算力，64 次自适应修订可超过 256 次并行采样的基线。
```

## Abstract

For PaLM 2-S* on MATH, the best allocation of generation budget across verifier search and sequential revision depends on model-relative problem difficulty. Difficulty-adaptive revision outperforms a parallel best-of-N baseline at 64 versus 256 samples. FLOPs-matched comparisons with a model roughly 14× larger favor test-time compute on easier questions or under lower inference load, but not in every regime.
