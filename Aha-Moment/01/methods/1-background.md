> [论文索引](../INDEX.MD) · 第 2 节

# Background：IO、CoT 与自洽

- **IO**：提示封装指令和可选示例，直接采样 $y\sim p_\theta^{IO}(y\mid x)$。
- **CoT**：在 $x$ 和最终答案 $y$ 之间生成 $z_1,\ldots,z_n$。模型按顺序采样各步骤；实际输出通常是一条连续文本，思维单元的边界没有显式定义。
- **CoT-SC**：独立采样 $k$ 条完整推理链，选择出现最多的答案。它比较末端答案，而不在同一条链的中途探索分支；投票也要求答案便于归并。

参见[框架图](../figures/figure-1-schematic.md)及 [ToT 方法](2-tree-of-thoughts.md)。
