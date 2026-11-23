> [返回论文索引](../INDEX.MD) · §5.2

# 预缓存与 look-ahead 不等同

在 The Pile 子集上学习线性映射 $W_{\mathrm{LA}}$，把当前位置残差流经冻结的语言头映射到更远 token 的预测（研究最多前瞻 5 个 token）。用该映射的前 $r$ 个右奇异向量组成子空间，估计各 SAE 方向与它的余弦相似度，再与 $Q(w)$ 计算相关。

所测前瞻映射普遍表现为负相关。预缓存程度高并不意味着更容易从当前残差流直接解码未来 token。作者认为这支持 breadcrumbs 假设：用于不同位置预测的特征相似可解释前瞻，不需等同于显式规划。

[图 7 Spearman](../figures/figure-7-look-ahead.md) · [图 20 Pearson](../figures/figure-20-pearson.md) · [实验细节](../appendix/4-experimental-details.md)
