> [返回论文索引](../INDEX.MD) · §2、§3.2

# 模型和非统一复杂度类

论文考察固定层数的 decoder-only Transformer，由 token/位置嵌入、因果 softmax 自注意力、残差前馈层及输出层组成。生成后的 token 附加到输入，再运行下一轮；零步 CoT 就是一次前向后作答。

记 $\mathsf{CoT}[T(n),d(n),s(n),e(n)]$ 为这样的判定问题族：存在统一的常数深度，对每个输入长度 $n$ 可以选择一套参数，用 $O(T(n))$ 个中间 token、$O(d(n))$ 的嵌入宽度、$O(s(n))$ 的尾数精度和 $O(e(n))$ 个指数位正确处理该长度的所有字符串。记 $\mathsf T[d,s,e]=\mathsf{CoT}[0,d,s,e]$；省略 $e$ 表示固定点（零个指数位）。

非统一允许不同长度采用不同参数和位置表，因而不能把本篇的 P/poly 直接视为 [Merrill 与 Sabharwal](../../02/INDEX.MD) 对统一模型给出的 P。实验也不是用一个模型外推任意长度。

[模型算法原文](../../../TeX/Chain-of-Thought/arXiv-2402.12875v4/preliminary.tex) · [有限精度](2-finite-precision.md)
