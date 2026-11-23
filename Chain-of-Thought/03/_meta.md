> [返回论文索引](INDEX.MD)

# _meta

```meta
paper_id: 03
status: done
title: Chain of Thought Empowers Transformers to Solve Inherently Serial Problems
lang: en
journal: ICML
year: 2024
doi:
authors_short: Li et al.
keywords: chain of thought; circuit complexity; finite precision; serial computation; transformer expressiveness
one_liner: 常数精度、对数宽度的非统一模型可用 O(T) 步模拟 T 门布尔电路；对数步在该精度模型下仍受 AC⁰ 限制。
```

## Abstract

With iterative rounding, constant-depth models of constant precision and exponent bits stay in AC⁰ with up to logarithmically many decoding steps. With O(log n) embedding width and constant precision, T steps can simulate size-T Boolean circuits, giving P/poly for polynomially many steps in the non-uniform setting. Synthetic tasks contrast direct prediction, intermediate supervision without recurrence, and autoregressive CoT.
