> [返回论文索引](../INDEX.MD) · 结论与附录

# 结论及适用范围

CoT 写回把单次前向的并行计算连成多次串行计算，能解释为何复杂多步任务可明显受益。只给 Hint 虽也改善监督，却不使后续注意力获得已预测的计算结果。实验和定理的模型不同：实验为固定宽度、float16 和有限长度，理论界讨论渐近资源。

非统一表达能力不保证一个训练好的模型能外推到所有长度。附录指出，若要求参数可由图灵机以多项式时间生成，则相应多项式步模型达到 P，而不是非统一的 P/poly。另有关于 LayerNorm 与多头注意力的架构扩展讨论。

[结论原文](../../../TeX/Chain-of-Thought/arXiv-2402.12875v4/conclusion.tex) · [相关工作](../../../TeX/Chain-of-Thought/arXiv-2402.12875v4/additional_related_works.tex) · [非统一讨论](../../../TeX/Chain-of-Thought/arXiv-2402.12875v4/appendix_non_uniformity.tex)
