> ⬅️ 返回 [论文索引](INDEX.MD)

# Paper manifest

```meta
paper_id: 02
status: done
title: Scaling Monosemanticity: Extracting Interpretable Features from Claude 3 Sonnet
lang: en
journal: Transformer Circuits Thread
year: 2024
doi: 10.48550/arXiv.2605.29358
authors_short: Templeton et al.
keywords: sparse autoencoders; dictionary learning; mechanistic interpretability; feature steering; superposition; Claude 3 Sonnet
one_liner: 在 Claude 3 Sonnet 中间层训练最多约 3400 万特征槽的稀疏自编码器，提取出部分跨语言和模态、能通过干预改变输出的可解释特征，但字典并不完备。
```

## Abstract

**Background:** Can unsupervised dictionary learning find interpretable directions in a production-scale language model?

**Methods:** Train sparse autoencoders on the middle residual stream of Claude 3 Sonnet, with widths of about 1M, 4M and 34M. Use scaling laws to allocate compute, and assess features with examples, automated interpretation, clamping and ablation.

**Results:** All three reconstructions explain at least 65% of the residual activations’ variance and use fewer than 300 active features per token on average. Selected features generalize across languages, from text to images, and from concrete examples to abstract references. Feature manipulations influence some completions. Larger dictionaries recover more rare concepts, but coverage remains incomplete.

**Interpretation:** Large-scale dictionaries expose useful candidate representations and some causally relevant intermediate features. The experiments do not establish a complete or faithful account of the model's computation.
