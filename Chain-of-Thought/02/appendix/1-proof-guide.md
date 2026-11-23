> [返回论文索引](../INDEX.MD) · 附录 A–E

# 证明附录导读

| 节 | 内容与在主证明中的作用 |
|---|---|
| A Transformer Components | 定义 projected pre-norm 和 multi-pre-norm 并给出分层模拟，定义嵌入、注意力打分与激活块。 |
| B Turing Machines | 明确多带机的配置、一次转移、初始条件及停机输出。 |
| C Layer-Norm Hash | 四维零均值向量的比例不变性、匹配内积，以及平均后的向量仍等于查询哈希所需的条件。 |
| D Input Tape Retrieval | 输入有效地址时注意力命中唯一位置，返回正确符号；越界时平均结果不等于查询哈希，故可返回空白。 |
| E Rightmost Retrieval | 查询键先按地址匹配，再加位置排序项；排序幅度受控，不能胜过地址不匹配造成的内积差，因此返回最近写入。 |

[完整附录 TeX](../../../TeX/Chain-of-Thought/arXiv-2310.07923v5/appendix.tex) · [模型定义](../methods/1-transformer-decoder.md) · [图灵机构造](../results/3-turing-machines.md)
