# Chain of Thought Empowers Transformers to Solve Inherently Serial Problems

> [合集索引](../INDEX.MD) · Level 1 · ICML 2024 · [arXiv:2402.12875v4](https://arxiv.org/abs/2402.12875v4) · [本地主 TeX](../../TeX/Chain-of-Thought/arXiv-2402.12875v4/main.tex)

## 摘要（Abstract）

Instructing the model to generate a sequence of intermediate steps, *a.k.a.*, a chain of thought (CoT), is a highly effective method to improve the accuracy of large language models (LLMs) on arithmetics and symbolic reasoning tasks. However, the mechanism behind CoT remains unclear. This work provides a theoretical understanding of the power of CoT for decoder-only transformers through the lens of expressiveness. Conceptually, CoT empowers the model with the ability to perform inherently serial computation, which is otherwise lacking in transformers, especially when depth is low. Given input length $n$, previous works have shown that constant-depth transformers with finite precision $\mathsf{poly}(n)$ embedding size can only solve problems in $\mathsf{TC}^0$ without CoT. We first show an even tighter expressiveness upper bound for constant-depth transformers with constant-bit precision, which can only solve problems in $\mathsf{AC}^0$, a proper subset of $\mathsf{TC}^0$. However, with $T$ steps of CoT, constant-depth transformers using constant-bit precision and $O(\log n)$ embedding size can solve any problem solvable by boolean circuits of size $T$. Empirically, enabling CoT dramatically improves the accuracy for tasks that are hard for parallel computation, including the composition of permutation groups, iterated squaring, and circuit value problems, especially for low-depth transformers.

## 关键结论

常数精度、常数指数位的模型在对数步预算内仍落在 AC⁰；常数精度和对数嵌入宽度允许每步模拟一个布尔门，在非统一设定中多项式步数给出 P/poly。实验以 Hint 区分中间监督和自回归写回。

## 章节导航

- [作者与机构](front-matter/authors-affiliations.md) · [元数据](_meta.md) · [引言](introduction/introduction.md)
- [Transformer 与 CoT 定义](methods/1-transformer-and-cot.md) · [有限精度](methods/2-finite-precision.md) · [合成实验协议](methods/3-experimental-setup.md) · [电路复杂度术语](methods/4-circuit-complexity.md)
- [精度与上界](results/1-upper-bounds.md) · [模拟布尔电路与 S₅ 分离](results/2-circuit-simulation.md) · [宽度与 oracle 门](results/3-oracle-gates.md) · [模加法](results/4-modular-addition.md) · [置换复合](results/5-permutations.md) · [迭代平方](results/6-iterated-squaring.md) · [电路求值](results/7-circuit-value.md)
- 图：[1 常数精度层级](figures/figure-1-constant-precision.md) · [2 电路模拟](figures/figure-2-circuit-simulation.md) · [3 S₅](figures/figure-3-permutations.md) · [4 C₇](figures/figure-4-modular-addition.md) · [5 迭代平方](figures/figure-5-iterated-squaring.md) · [6 电路求值](figures/figure-6-circuit-value.md) · [7 C₂](figures/figure-7-parity.md) · [8 串行任务 Base](figures/figure-8-serial-base.md) · [9 模加法 Base](figures/figure-9-modular-base.md) · [10 对数精度层级](figures/figure-10-log-precision.md)
- [附录证明与补充实验](appendix/1-proof-and-experiment-guide.md) · [结论及适用范围](discussion/conclusions.md) · [参考文献](references/references.md)
