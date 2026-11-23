> ⬅️ 返回 [论文索引](INDEX.MD)

# Paper manifest

```meta
paper_id: 01
status: done
title: Toy Models of Superposition
lang: en
journal: Transformer Circuits Thread
year: 2022
doi: 10.48550/arXiv.2209.10652
authors_short: Elhage et al.
keywords: superposition; polysemanticity; sparsity; privileged basis; compressed sensing
one_liner: 在输出带 ReLU 的玩具模型中，90% 稀疏度下，五个特征在二维空间排成五边形，但会产生干扰。
```

## Abstract

**Background:** A single neuron can respond to unrelated features. Superposition is one proposed explanation: an activation space can represent more features than it has dimensions.

**Methods:** Train low-dimensional ReLU toy networks to reconstruct or compute the elementwise absolute value of synthetic features. Vary sparsity, loss weights, and which features tend to co-occur.

**Results:** Dense inputs favor dedicated directions. In the five-feature, two-dimensional example, 80% sparsity leads to two antipodal pairs and 90% sparsity leads to a pentagon. The learned geometry changes with sparsity, importance and co-occurrence. Some networks can approximate absolute value on features represented in superposition.

**Interpretation:** These experiments establish that superposition and polysemanticity can arise in simple neural networks. The degree to which specific geometries and dynamics generalize is open.
