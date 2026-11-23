# Tree of Thoughts — 元数据

> [论文索引](INDEX.MD)

```meta
paper_id: 01
status: done
title: Tree of Thoughts: Deliberate Problem Solving with Large Language Models
lang: en
journal: NeurIPS
year: 2023
doi:
authors_short: Yao et al.
keywords: tree of thoughts; heuristic search; test-time inference
one_liner: GPT-4 上的显式思维树搜索把 24 点成功率从 CoT 的 4% 提升到 74%，无需额外训练。
```

## Abstract

The paper reorganizes language-model inference as heuristic search over coherent intermediate thoughts. The model generates and evaluates candidate states; an external breadth-first or depth-first controller selects, prunes, or backtracks. In three GPT-4 tasks, ToT improves Game of 24 success, creative-writing coherence, and mini-crossword completion, at increased inference cost.
