# The Expressive Power of Transformers with Chain of Thought

> [合集索引](../INDEX.MD) · Level 1 · ICLR 2024 · [arXiv:2310.07923v5](https://arxiv.org/abs/2310.07923v5) · [本地主 TeX](../../TeX/Chain-of-Thought/arXiv-2310.07923v5/CoT-Decoders.tex)

| 项目 | 内容 |
|---|---|
| 研究类型 | 统一的 decoder-only Transformer 表达能力 |
| 主要变量 | 输入长度为 $n$ 时允许的中间解码步数 $t(n)$ |
| 核心发现 | 对数步仍在 L 中；线性步可识别所有正则语言；多项式步在指定架构下恰好覆盖 P |

## 摘要（Abstract）

Recent theoretical work has identified surprisingly simple reasoning problems, such as checking if two nodes in a graph are connected or simulating finite-state machines, that are provably unsolvable by standard transformers that answer immediately after reading their input. However, in practice, transformers' reasoning can be improved by allowing them to use a “chain of thought” or “scratchpad”, i.e., generate and condition on a sequence of intermediate tokens before answering. Motivated by this, we ask: *Does such intermediate generation fundamentally extend the computational power of a decoder-only transformer?* We show that the answer is *yes*, but the amount of increase depends crucially on the amount of intermediate generation. For instance, we find that transformer decoders with a logarithmic number of decoding steps (w.r.t. the input length) push the limits of standard transformers only slightly, while a linear number of decoding steps, assuming projected pre-norm (a slight generalization of standard pre-norm), adds a clear new ability (under standard complexity conjectures): recognizing all regular languages. Our results also imply that linear steps keep transformer decoders within context-sensitive languages, and polynomial steps with generalized pre-norm make them recognize exactly the class of polynomial-time solvable problems—the first exact characterization of a type of transformers in terms of standard complexity classes. Together, this provides a nuanced framework for understanding how the length of a transformer’s chain of thought or scratchpad impacts its reasoning power.

## 章节导航

- [作者与机构](front-matter/authors-affiliations.md) · [元数据](_meta.md) · [研究问题](introduction/introduction.md)
- [模型与精度](methods/1-transformer-decoder.md) · [Layer-Norm Hash](methods/2-layer-norm-hash.md)
- [能力总览](results/1-expressiveness.md) · [有限自动机](results/2-automata.md) · [图灵机模拟](results/3-turing-machines.md) · [时间与空间上界](results/4-upper-bounds.md)
- [图 1：复杂度层级](figures/figure-1-hierarchy.md) · [附录证明路线](appendix/1-proof-guide.md) · [结论与开放问题](discussion/conclusions.md) · [参考文献](references/references.md)
